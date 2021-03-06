# Pre-Operation Events
ACMA provides the ability to send events to objects in the database prior to an full import, delta import, or export operation. 

Pre-operation events allow you to define a [[database query]] that searches for objects matching your criteria, and sends them an event. [[Event rules | event rule]] can be used to trigger constructors to execute in response to these events. Once all events have been processed, ACMA resumes the FIM import or export operation.

## Use cases
ACMA isn't running at all times, it is only active when invoked by the FIM synchronization service. Due to this aspect of the design, ACMA can't natively respond to _temporal_ changes.
While most constructors have execution rules that depend on the changing state of an object, (which is directly driven by FIM), rules that compare a DateTime value need to be evaluated outside of the object change process.

A temporal rule, such as _expiryDate greater than today_ requires a trigger at the time the expiry date becomes greater than the current date. Neither the FIM synchronization service or ACMA have any temporal evaluation capability built in. Pre-operation events provide a way around this limitation. They perform a database query before each FIM operation and send events to objects that match the query.

For example, if we had a pre-operation event that search for _all objects with an expiryDate greater than today_, ACMA can find these objects and send an _expiryDateLapsed_ event to them. This allows you to define constructors that look for this event (using an [[event rule]]), and perform the appropriate actions, such as disabling the account.

With appropriate indexing, pre-operation events execute very quickly, and do not significantly increase the start-up time of the MA.

## Alternatives
The alternative to using pre-operation events, is to use the [[ACMA powershell cmdlets | powershell]], and run a scheduled task once a day to find expired objects and either send the _expiryDateLapsed_ event from there, or modify the appropriate attribute values yourself.

The correct solution depends on your environment. If you require only daily temporal updates, you can use the script method. If you want more frequent updates, pre-operation events provide the best way to do this.


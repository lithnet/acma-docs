# Exit events
Exit events are a powerful feature that allows you to perform actions external to the object being exported. 

Once an export operation has completed for an individual object, the exit events in the class constructor are evaluated against the exported object in its final state. If any of the event conditions are met, the event is raised, and processing of that event begins. Different types of events perform different actions.

## Internal exit events
[[Internal exit events]] are used to send an event to other objects in the ACMA database. The internal event defines the recipients of the raised event. The event can be sent to an object referenced by the triggering object, or a [[database query]] can be performed to send the event to any object in the database. The receiving object then has an opportunity to process the event with an [[event rule]].

## External exit events (command)
[[Command exit events]] allow you to execute an external process when an event is raised. Attributes from the triggering object can be passed to the process as arguments.
## External exit events (extension)
[[Extension exit events]] allow you to write your own custom C# code that will be executed by ACMA when an event is raised. See the [[extension exit events]] topic for details on implementing the interfaces required to support these events.


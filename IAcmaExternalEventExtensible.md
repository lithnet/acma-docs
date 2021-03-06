# IAcmaExternalEventExtensible
The IAcmaExternalEventExtensible interface is implemented by an extensible external event to perform a custom action
## Interface Members
### Methods
#### OnEventRaised(RaisedEvent raisedEvent, MAObjectHologram sender)
The OnEventRaised method is called by the ACMA engine when it has determined that the execution conditions for an event have been met. The sender parameter contains the object that the event will be raised for. 

This method provides your code an opportunity to examine the hologram before the object is commited to the database. This allows you to see both current and proposed attribute values of the object. You can save any custom configuration in the RaisedEventProperties dictionary on the raisedEvent object.

Do not perform the external action in this section of code. If you do not need to perform any pre-processing of the object, you can simply implement an empty method.

#### Execute(RaisedEvent raisedEvent)
The Execute method is called when ACMA is ready for the extension to perform the external command. Items added to the RaisedEventProperties of the raisedEvent in OnEventRaised will be passed back to your function for evaluation. 


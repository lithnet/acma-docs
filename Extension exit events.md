# Extension exit events
ACMA allows you to create your own custom exit event to perform an action when an event is raised. Extension events are written in .NET (either C# or VB.NET). Extension events implement the [[Lithnet.Acma.IAcmaExternalEventExtensible | IAcmaExternalEventExtensible]] interface.
## Parameters
### Event name
All events must have a unique name that is used to identify the event
### Event is disabled
Events can be disabled to prevent them from being raised and executed
### Extension path
The path to the DLL containing the class that implements [[IAcmaExternalEventExtensible]]
### Class name
The name of the class that implements [[IAcmaExternalEventExtensible]]
### Execute event asynchronously
The extensible event can either be run synchronously or asynchronously, In synchronous mode, ACMA will wait for the event to complete before moving onto the next export object. In asynchronous mode, ACMA will run extensible events on a separate thread, and continue to process export objects. ACMA will wait until all operations have completed before signaling to the FIM sync engine that the export has completed.
### On error
When exporting synchronously, you can abort the export operation on the object, and return an error to the sync engine. When exporting asynchronously, you can only log the error to the ACMA log file.


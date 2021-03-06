# Internal exit events
Internal exit events provide a way for one ACMA object to send an event to another. A class constructor generates internal exit events when it has completed processing an object export. The internal exit event defines recipients that should receive the event.
As with all events, the [[execution conditions | rules]] must be met for the event to be raised.
## Parameters
### Event name
All events must have a unique name that is used by an [[event rule]] to trigger an action
### Event is disabled
Events can be disabled to prevent them from being raised and sent to other objects
### Referenced recipients
Events can be sent to one or recipients that are relative to the object being processed by the class constructor. Simply select the reference attributes containing the event recipients.
### Recipient queries
When an event needs to be sent to an object that is not referenced by the object being processed, a standard [[database query]] can be used to find relevant recipients. 


# Event rule
The event rule can be used to detect an [[exit event | exit events]] or [[pre-operation event | pre-operation events]] that has been raised and sent to this object under evaluation.
An event is a simple construct consisting of a name, and a sender. An event rule will trigger if the event name matches that of the raised event.
Optionally, you can further constrain the rule to match a particular sender, but only if the object under evaluation has a reference to the object that sent the event.


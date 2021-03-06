# Command exit events
Command exit events provide a way for a class constructor to call an external program in response to specified conditions being met. Any command line application can be executed.
As with all events, the [[execution conditions | rules]] must be met for the event to be raised.
## Parameters
### Event name
All events must have a unique name that is used to identify the event
### Event is disabled
Events can be disabled to prevent them from being raised and executed
### Command to execute
Specify the path and executable file to run
### Arguments
The command-line arguments to pass the executable. Please note that as this uses [[ACMA DL | ACMA declarative language]], certain characters must be escaped to be passed to the command line.
### Execute event asynchronously
The external command can either be run synchronously or asynchronously, In synchronous mode, ACMA will wait for the process to exit before moving onto the next export object. In asynchronous mode, ACMA will run external commands on a separate thread, and continue to process export objects. ACMA will wait until all operations have completed before signaling to the FIM sync engine that the export has completed.
### On error
When exporting synchronously, you can abort the export operation on the object, and return an error to the sync engine. When exporting asynchronously, you can only log the error to the ACMA log file.

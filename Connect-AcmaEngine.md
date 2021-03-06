# Connect-AcmaEngine
## Description
The Connect-AcmaEngine cmdlet connects to the ACMA database and must be run before any database operations. The cmdlet is used to specify not only the database to connect to, but what configuration file to use. When changes are made to an object, the constructors in the configuration file are executed on the object.
## Syntax
```
Connect-AcmaEngine -DatabaseName <string> -ServerName <string> -ConfigFile <string> [[-LogFile]] <string> [[-LogLevel None | Info | Error | Warning | DetailedInfo | Debug]]
```
## Parameters
### DatabaseName
The name of the database to connect to
### ServerName
The name of the SQL server where the database is hosted
### ConfigFile
The full path to the ACMAX configuration file to load into the instance
### LogFile
Optional. The full path to the log file used for the session
### LogLevel
Optional. Specifies the level of detail written to the log file
## Examples
```
Connect-AcmaEngine -DatabaseName Lithnet.Acma -ServerName localhost -ConfigFile D:\MAData\ACMA\prod.acmax
```



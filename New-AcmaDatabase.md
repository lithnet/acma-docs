# New-AcmaDatabase
## Description
The New-AcmaDatabase creates a new, empty ACMA database on the specified server. You must have sysadmin rights on the SQL server in order to create a new database
## Syntax
```
New-AcmaDatabase -DatabaseName <string> -ServerName <string> 
```
## Parameters
### DatabaseName
The name of the database to create
### ServerName
The name of the SQL server where the database is to be created
## Examples
```
New-AcmaDatabase -DatabaseName Lithnet.Acma -ServerName localhost 
```



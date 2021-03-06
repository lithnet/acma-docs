# Update-AcmaDatabase
## Description
The Update-AcmaDatabase updates an ACMA database on the specified server to the latest version. You must have db_owner rights on the database to perform the update.
## Syntax
```
Update-AcmaDatabase -DatabaseName <string> -ServerName <string> 
```
## Parameters
### DatabaseName
The name of the database to update
### ServerName
The name of the SQL server where the database is to be stored
## Examples
```
Update-AcmaDatabase -DatabaseName Lithnet.Acma -ServerName localhost 
```
## Notes
While the MA installer will update the last installed database when run, other ACMA databases on the server do not get automatically updated. For example, is using the MA as an SQL data source, or having a separate unit test DB. This cmdlet allows you to manually update these databases.


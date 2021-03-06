# New-AcmaPresenceQuery 
## Description
Creates a new query that searches for the presence or absence of an attribute value. This cmdlet generates a DBQueryObject that can be used with the [[Get-AcmaObjects]] cmdlet
## Syntax
```
New-AcmaPresenceQuery -AttributeName<string> -Operator [[IsPresent | NotPresent]]
```
## Parameters
### AttributeName
The name of the attribute to query
### Operator
The type of presence search to perform. Valid values are IsPresent or NotPresent
## Return type
The cmdlet returns an AcmaDBQueryObject
## Examples
```powershell
$query = New-AcmaPresenceQuery -AttributeName "accountName" -Operator IsPresent
$objects = Get-AcmaObjects $query
```



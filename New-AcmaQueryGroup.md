# New-AcmaQueryGroup 
## Description
Creates a new group of query objects that search for objects in the database. This cmdlet generates a DBQueryObject that can be used with the [[Get-AcmaObjects]] cmdlet
## Syntax
```
New-AcmaQueryGroup -Operator [[All | Any | None | One]] -QueryObjects <DBQueryObject[]>
```
## Parameters
### Operator 
The type of operator to use on the contained query objects. 

| Value | Description |
| --- | --- |
| All | All contained queries must be satisfied for a match to be found |
| Any | Any of the contained queries must be satisfied for a match to be found |
| None | None of the contained queries must be satisfied for a match to be found |
| One | Only one of the contained queries must be successful for a match to be found |
### QueryObjects 
An array of query objects that were created with the [[New-AcmaQuery]], [[New-AcmaPresenceQuery]], or [[New-AcmaQueryGroup]] cmdlets
## Return type
The cmdlet returns an AcmaDBQueryObject
## Examples
```powershell
$query1 = New-AcmaQuery -AttributeName "department" -Operator Equals -Value "Finance";
$query2 = New-AcmaQuery -AttributeName "mail" -Operator EndsWith -Value "acma.com";
$query = New-AcmaQueryGroup -Operator All -QueryObjects @($query1, $query2);
$objects = Get-AcmaObjects $query
```



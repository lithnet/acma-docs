# Get-AcmaObjects
## Description
Gets the specified objects from the ACMA database
## Syntax
```
Get-AcmaObjects -DBQuery <AcmaPSDBQueryObject>
Get-AcmaObjects -IDs <guid[]>
```
## Parameters
### DBQuery
A DBQuery object created using the [[New-AcmaPresenceQuery]], [[New-AcmaQuery]], or [[New-AcmaQueryGroup]] cmdlets
### IDs
An array of object IDs 
## Return type
The cmdlet returns an collection of [[AcmaPSObjects | AcmaPSObject]]
## Examples
```powershell
$objects = Get-AcmaObjects -IDs @("e88035d4-0d45-4f2a-8cb1-d71aa55a7187","8f495b8d-799e-4eb1-9edf-dbe07fc01464");

$query = New-AcmaQuery -Attribute "objectClass" -Operator Equals -Value "person";
$objects =Get-AcmaObjects $query;
```



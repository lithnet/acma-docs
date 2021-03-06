# Remove-AcmaObject
## Description
Adds a new instance of an object class to the ACMA database
## Syntax
```
Remove-AcmaObject -ID <guid> [[-ForceDelete $true | $false]]
Remove-AcmaObject -AcmaObject <AcmaPSObject> [[-ForceDelete $true | $false]]
```
## Parameters
### ID
The object ID of the object to remove
### AcmaObject
The object to remove
### ForceDelete
Set force delete to true to permanently delete an object of a object class that is marked as undeletable. This setting an no effect on object classes that are not marked as undeletable.
## Examples
```powershell
Remove-AcmaObject -ID "8f495b8d-799e-4eb1-9edf-dbe07fc01464"
Get-AcmaObject -ID "8f495b8d-799e-4eb1-9edf-dbe07fc01464" | Remove-AcmaObject
```



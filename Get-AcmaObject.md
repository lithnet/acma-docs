# Get-AcmaObject
## Description
Gets an instance of an ACMA object from the database
## Syntax
```
Get-AcmaObject -ID <guid>
```
## Parameters
### ID
The object ID of the ACMA object
## Return type
The cmdlet returns a reference to the [[AcmaPSObject]]
## Examples
```powershell
$newObject = Get-AcmaObject -ID "8f495b8d-799e-4eb1-9edf-dbe07fc01464";
$newObject.ToString();
```



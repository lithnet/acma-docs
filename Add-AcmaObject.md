# Add-AcmaObject
## Description
Adds a new instance of an object class to the ACMA database
## Syntax
```
Add-AcmaObject -ObjectClass <string>
```
## Parameters
### ObjectClass
The name of the object class to create an instance of
## Return type
The cmdlet returns a reference to the newly created AcmaPSObject
## Examples
```powershell
$newObject = Add-AcmaObject -ObjectClass "person";
$newObject.ToString();
```



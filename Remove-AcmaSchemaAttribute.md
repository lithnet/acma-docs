# Remove-AcmaSchemaAttribute 
## Description
The Remove-AcmaSchemaAttribute cmdlet removes an attribute from the ACMA database.

The Remove-AcmaSchemaAttribute cmdlet can only be used when there are no active bindings for the attribute.
## Syntax
```
Remove-AcmaSchemaAttribute -Name<string>
```
## Parameters
### Name
The name of the attribute
## Examples
```powershell
Remove-AcmaSchemaAttribute -Name "accountName"
```



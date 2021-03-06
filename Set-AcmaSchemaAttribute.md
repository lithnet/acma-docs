# Set-AcmaSchemaAttribute
## Description
The Set-AcmaSchemaAttribute cmdlet allows you to change the index status or operation type of the attribute
## Syntax
```
Set-AcmaSchemaAttribute -Name<string> [[-IsIndexed $true | $false]] [[-Operation ImportOnly | ImportExport | ExportOnly | AcmaInternalTemp | AcmaInteral]] 
```
## Parameters
### Name
The name of the attribute to modify
### IsIndexed
Indicates if the attribute values are indexed. Boolean and non-indexable types cannot be indexed
### Operation
Defines the types of operations allowed on this attribute

| Operation | Description |
| --- | --- |
| AcmaInternal | The attribute is not visible to FIM |
| AcmaInternalTemp | The attribute is not visible to FIM, and its value is never saved to the database |
| ExportOnly | The attribute is visible to FIM, but can only be exported (write-only) |
| ImportExport | The attribute is visible to FIM, and can be imported and exported |
| ImportOnly | The attribute is visible to FIM, but can only be imported (read-only) |
## Examples
```powershell
Set-AcmaSchemaAttribute -Name "accountName" -IsIndexed $true
Set-AcmaSchemaAttribute -Name "accountName" -Operation ImportOnly
```



# Add-AcmaSchemaAttribute 
## Description
The Add-AcmaSchemaAttribute cmdlet creates a new attribute in the ACMA database
## Syntax
```
Add-AcmaSchemaAttribute -Name<string> -Type Binary | BinaryNotIndexable | Boolean | DateTime | Integer | Reference | String | StringNotIndexable -IsMultivalued $true | $false -IsIndexed $true | $false -Operation ImportOnly | ImportExport | ExportOnly | AcmaInternalTemp | AcmaInteral
```
## Parameters
### Name
The name of the attribute
### Type
The data type of the attribute

| Type | Description |
| --- | --- |
| Binary | A binary value up to 800 bytes in length |
| BinaryNotIndexable | A binary value over 800 bytes in length |
| Boolean | A Boolean value |
| DateTime | A date and time value |
| Integer | A 64-bit integer value |
| Reference | A reference-type value |
| String | A string value up to 400 characters in length |
| StringNotIndexable | A string value over 400 characters in length |

### IsMultivalued
Indicates if the attribute contains multiple values. This is not valid for Boolean values.
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
Add-AcmaSchemaAttribute -Name "accountName" -Type String -IsMultivalued $false -IsIndexed $true -Operation ImportExport
Add-AcmaSchemaAttribute -Name "accountDisabled" -Type Boolean -IsMultivalued $false -IsIndexed $false -Operation ImportExport
```



# Remove-AcmaSchemaBinding 
## Description
The Remove-AcmaSchemaBinding cmdlet removes an attributebinding from an object class.
*WARNING:* Removing a binding will delete all values contained in the attribute on that object class.
## Syntax
```
Remove-AcmaSchemaBinding -Attribute <string> -ObjectClass <string>
```
## Parameters
### Attribute
The name of attribute
### ObjectClass
The name of the object class
## Examples
```powershell
Remove-AcmaSchemaBinding -Attribute "accountName" -ObjectClass "person"
```



# Add-AcmaSchemaBinding 
## Description
The Add-AcmaSchemaBinding cmdlet creates a binding of an attribute to an object class. Bindings can be static, or inherited from a referenced object present on the object class. An inherited binding becomes read-only and is automatically updated when the referenced attribute changes.
## Syntax
```
Add-AcmaSchemaBinding -Attribute <string> -ObjectClass <string>
Add-AcmaSchemaBinding -Attribute <string> -ObjectClass <string> -InheritanceSourceClass <string> -InheritanceSourceReference <string -InheritanceSourceAttribute <string>
```
## Parameters
### Attribute
The name of the attribute to bind to the object class
### ObjectClass
The name of the object class to bind the attribute to
### InheritanceSourceReference
The attribute on the object that contains a reference value to inherit from
### InheritanceSourceClass
The type of object that the InheritanceSourceReference references
### InhertianceSourceAttribute
The attribute on the referenced object to inherit
## Examples
```powershell
Add-AcmaSchemaBinding -Attribute "accountName" -ObjectClass "person"
Add-AcmaSchemaBinding -Attribute "orgUnitName" -ObjectClass "person" -InheritanceSourceReference "orgUnit" -InhertianceSourceClass "organizationalUnit" -InheritanceSourceAttribute "displayName"
```



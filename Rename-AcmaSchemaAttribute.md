# Rename-AcmaSchemaAttribute 
## Description
The Rename-AcmaSchemaAttribute cmdlet renames an attribute in the ACMA database
*WARNING:* Renaming an attribute in the database will not rename it in any configuration files, which may render the configuration file unable to be opened. It is recommended to open the configuration file in the ACMA editor, and rename the attribute using the UI. The ACMA editor will update the references to the attribute in the ACMAX file with the new names when you save the configuration file.
## Syntax
```
Rename-AcmaSchemaAttribute -CurrentName<string> -NewName <string>
```
## Parameters
### CurrentName
The current name of the attribute
### NewName
The new name of the attribute
## Examples
```powershell
Rename-AcmaSchemaAttribute -CurrentName "accountName" -NewName "samAccountName"
```



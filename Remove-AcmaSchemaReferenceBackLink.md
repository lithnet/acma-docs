# Remove-AcmaSchemaReferenceBackLink 
## Description
Removes a back-link from the ACMA database schema
## Syntax
```
Remove-AcmaSchemaReferenceBackLink -SourceObjectClass <string> -SourceAttribute <string> -TargetObjectClass <string> -TargetAttribute <string>
```
## Parameters
## Parameters
### SourceObjectClass 
The name of the object class that is the source of the back-link
### SourceAttribute 
The name of the reference attribute that contains the target of the back-link
### TargetObjectClass 
The name of the object class that is the target of the back-link
### TargetAttribute 
The name of the reference attribute that is the target of the back-link
## Examples
```powershell
Remove-AcmaSchemaReferenceBackLink -SourceObjectClass "person" -SourceAttribute "manager" -TargetObjectClass "person" -TargetAttribute "directReports"
```



# Add-AcmaSchemaReferenceBackLink 
## Description
Creates a new back-link in the ACMA database schema
## Syntax
```
Add-AcmaSchemaReferenceBackLink -SourceObjectClass <string> -SourceAttribute <string> -TargetObjectClass <string> -TargetAttribute <string>
```
## Parameters
### SourceObjectClass 
The name of the object class that is the source of the back-link
### SourceAttribute 
The name of the attribute that contains the reference to back-link to
### TargetObjectClass 
The name of the object class that is the target of the back-link
### TargetAttribute 
The name of the attribute that is the target of the back-link
## Examples
The following example links the `manager` attribute to the `directReports` attribute on the target. Whenever a person object's `manager` is changed, the `directReports` attribute of the manager will be updated.
```powershell
Add-AcmaSchemaReferenceBackLink -SourceObjectClass "person" -SourceAttribute "manager" -TargetObjectClass "person" -TargetAttribute "directReports"
```


asd
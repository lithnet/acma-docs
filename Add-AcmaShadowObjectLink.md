# Add-AcmaShadowObjectLink 
## Description
Creates a new shadow link in the ACMA database schema
## Syntax
```
Add-AcmaShadowObjectLink -Name <string> -ShadowObjectClass <string> -ReferenceAttribute <string> -ProvisioningAttribute <string>
```
## Parameters
### Name 
The unique name of the shadow link
### ShadowObjectClass 
The name of the shadow object class to create the link for
### ReferenceAttribute 
The name of the reference attribute on the shadow parent that contains the reference to the shadow object
### ProvisioningAttribute 
The name of the Boolean attribute on the shadow parent that controls the creation and deletion of the shadow object
## Examples
```powershell
Add-AcmaShadowObjectLink -Name "adminAccountLink" -ShadowObjectClass "shadowAdminAccount" -ReferenceAttribute "adminAccount" -ProvisioningAttribute "hasAdminAccount"
```



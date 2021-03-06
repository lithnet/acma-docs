# PowerShell cmdlets
ACMA comes with a set of PowerShell cmdlets that are installed with the UI component. These cmdlets can be used to modify both the ACMA database schema, as well as objects within the database.

The [[PowerShell Quick Reference Guide]] contains the most commonly used commands and example scripts.
## Full Cmdlet Reference
### Common cmdlets

- [[Connect-AcmaEngine]]
- [[Invoke-AcmaUnitTests]]
- [[New-AcmaDatabase]]
- [[Update-AcmaDatabase]]

### Database schema cmdlets
#### Constants

- [[Add-AcmaConstant]]
- [[Get-AcmaConstantValue]]
- [[Remove-AcmaConstant]]
- [[Set-AcmaConstantValue]]

#### Attributes

- [[Add-AcmaSchemaAttribute]]
- [[Remove-AcmaSchemaAttribute]]
- [[Rename-AcmaSchemaAttribute]]
- [[Set-AcmaSchemaAttribute]]

#### Bindings

- [[Add-AcmaSchemaBinding]]
- [[Remove-AcmaSchemaBinding]]

#### Back-links
- [[Add-AcmaSchemaReferenceBackLink]]
- [[Remove-AcmaSchemaReferenceBackLink]]

#### Sequences

- [[Add-AcmaSequence]]
- [[Remove-AcmaSequence]]
- [[Set-AcmaSequence]]

#### Shadow links

- [[Add-AcmaShadowObjectLink]]
- [[Remove-AcmaShadowObjectLink]]

### ACMA Object cmdlets
#### Object opreations

- [[Add-AcmaObject]]
- [[Remove-AcmaObject]]
- [[Get-AcmaObject]]
- [[Get-AcmaObjects]]

#### Object queries

- [[New-AcmaPresenceQuery]]
- [[New-AcmaQuery]]
- [[New-AcmaQueryGroup]]

#### XML Import and Export

- [[Export-AcmaObjects]]
- [[Import-AcmaObjects]]

#### Unit tests

- [[Invoke-AcmaUnitTests]]


# Export-AcmaObjects 
## Description
Exports the specified ACMA objects to an XML file
## Syntax
```
Export-AcmaObjects -FileName <string> -ExportObjects <AcmaPSObjects[]>
```
## Parameters
### FileName
The name of the file to export the entries to
### ExportObjects
The objects to export to the XML file
## Examples
```powershell
$query = New-AcmaQuery -Attribute "objectClass" -Operator Equals -Value "person";
$objects =Get-AcmaObjects $query;
Export-AcmaObjects -FileName "D:\temp\exported objects.xml" -ExportObjects $objects

$query = New-AcmaQuery -Attribute "objectClass" -Operator Equals -Value "person";
Get-AcmaObjects $query | Export-AcmaObjects -FileName "D:\temp\exported objects.xml";
```



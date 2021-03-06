# New-AcmaQuery 
## Description
Creates a new query that searches for a particular attribute value. This cmdlet generates a DBQueryObject that can be used with the [[Get-AcmaObjects]] cmdlet
## Syntax
```
New-AcmaQuery -AttributeName<string> -Operator [[Contains | EndsWith | Equals | GreaterThan | GreaterThanOrEq | LessThan | LessThanOrEq | NotContains | NotEquals | StartsWith]] -Value <string>
```
## Parameters
### AttributeName
The name of the attribute to query
### Operator
The type of presence search to perform. Valid values depend on the type of the target attribute
## Return type
The cmdlet returns an AcmaDBQueryObject
## Examples
```powershell
$query = New-AcmaQuery -AttributeName "accountName" -Operator StartsWith -Value "r"
$objects = Get-AcmaObjects $query
```

```powershell
$query = New-AcmaQuery -AttributeName "deleted" -Operator GreaterThan -Value 0
$objects = Get-AcmaObjects $query
```

```powershell
$query = New-AcmaQuery -AttributeName "department" -Operator Equals -Value "Finance"
$objects = Get-AcmaObjects $query
```



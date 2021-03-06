# Set-AcmaSequence 
## Description
Modifies the settings of a sequence in the ACMA database
## Syntax
```
Set-AcmaSequence -Name <string> -StartValue <int64> -MinValue <int64> -MaxValue <int64> -IncrementBy <int64>
Set-AcmaSequence -Name <string> -StartValue <int64> -IncrementBy <int64>
```
## Parameters
### Name 
The name of the sequence
### StartValue 
The value that the sequence should start from
### MinValue 
The minimum value when used in a cycling sequence
### MaxValue 
The maximum value when used in a cycling sequence
### IncrementBy 
The number to increment by with each call to the sequence
## Examples
The following example modifies a sequence so that starts at 5, increments by 1, and reaches a maximum value of 50 before starting back from 1.
```powershell
Set-AcmaSequence -Name "homeFolderGroup" -StartValue 5 -MinValue 1 -MaxValue 50 -IncrementBy 1
```

The following example modifies a sequence so that the next time it is called, it will start at 40,000 and increment continually by 1.
```powershell
Set-AcmaSequence -Name "unixUid" -StartValue 40000 -IncrementBy 1
```



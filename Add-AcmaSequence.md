# Add-AcmaSequence 
## Description
Creates a new sequence in the ACMA database
## Syntax
```
Add-AcmaSequence -Name <string> -StartValue <int64> -MinValue <int64> -MaxValue <int64> -IncrementBy <int64>
Add-AcmaSequence -Name <string> -StartValue <int64> -IncrementBy <int64>
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
The following example creates a sequence that starts at 1, increments by 1, and reaches a maximum value of 10 before starting back from 1.
```powershell
Add-AcmaSequence -Name "homeFolderGroup" -StartValue 1 -MinValue 1 -MaxValue 10 -IncrementBy 1
```

The following example creates a sequence that starts at 20,000 and increments continually by 1.
```powershell
Add-AcmaSequence -Name "unixUid" -StartValue 20000 -IncrementBy 1
```



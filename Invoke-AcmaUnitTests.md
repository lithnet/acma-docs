# Invoke-AcmaUnitTests
## Description
The Invoke-AcmaUnitTests cmdlet executes all unit tests in the configuration file loaded by the [[Connect-AcmaEngine]] cmdlet
## Syntax
```
Invoke-AcmaUnitTests [[-BreakOnTestFailure <boolean>]] [[-HtmlReportFileName <string>]]
```
## Parameters
### BreakOnTestFailure
Optional. Executes the unit tests, but stops the test run if a unit test fails.
### HtmlReportFileName
Optional. The full path to a file where the unit test results will be stored in HTML format
## Examples
```
Invoke-AcmaUnitTests
Invoke-AcmaUnitTests -BreakOnTestFailure $true
Invoke-AcmaUnitTests -HtmlReportFileName C:\temp\unit-test-results.html
```



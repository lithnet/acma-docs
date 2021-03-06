# PowerShell Quick Reference Guide
This guide contains the most commonly used cmdlets and examples on how to use them
## Importing the PowerShell module
Before use, the PowerShell module must first be imported into the session
```powershell
Add-PSSnapIn acmacmdlets
```

## Connecting to the database
All operations require that you first connect to the ACMA database and load an appropriate configuration file.
```powershell
Connect-AcmaEngine -DatabaseName Lithnet.Acma -ServerName localhost -ConfigFile D:\MAData\Acma\acma-prod.acma.xml
```

You can also specify logging settings using the `Connect-AcmaEngine` cmdlet
```powershell
Connect-AcmaEngine -DatabaseName Lithnet.Acma -ServerName localhost -ConfigFile D:\MAData\Acma\acma-prod.acma.xml -LogFile D:\MAData\Acma\ps.log -LogLevel Debug
```

## Getting a single object from the database
Once you have connected to the database, you can get an object from the database by specifying its object ID
```powershell
Get-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2"
```

## Getting multiple objects from the database
You can retrieve multiple objects by passing in an array of object IDs
```powershell
$ids = @("153e0873-502c-4edf-9df1-1e39ae4889e2", "e3737fbb-7ea2-42a1-8a22-dadadbe1aa80")
Get-AcmaObjects -IDs $ids
```

## Searching for an object
The PowerShell commands allow you to specify search criteria to find an object.
This example returns all objects of the 'person' object class
```powershell
$query = New-AcmaQuery -AttributeName "objectClass" -Operator equals -Value "person"
Get-AcmaObjects $query
```

The same command can be expressed as 
```powershell
New-AcmaQuery -AttributeName "objectClass" -Operator equals -Value "person" | Get-AcmaObjects
```

When querying the presence of an attribute, you can use the `New-AcmaPresenceQuery` cmdlet
```powershell
New-AcmaPresenceQuery -AttributeName "accountName" -Operator IsPresent -Value Get-AcmaObjects
```

You can use multiple search criteria in a query by creating a query group. The following example returns all objects of the person class that have been deleted. Nested groups are also supported.
```powershell
$query1 = New-AcmaQuery -AttributeName "objectClass" -Operator Equals -Value "person"
$query2 = New-AcmaQuery -AttributeName "deleted" -Operator NotEquals -value "0"
$queryGroup = New-AcmaQueryGroup -Operator All -QueryObjects @($query1, $query2)
Get-AcmaObjects $queryGroup
```

## Getting an attribute value
Once you have an AcmaObject, you can get the values of its attributes. To return the accountName attribute, you can call the following command
```powershell
$obj = Get-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2"
$obj.Attributes["accountName"]
```

## Setting an attribute value
You can set the value of a single valued attribute by passing in an array of new values. For single-valued attributes, you must pass in an array with only a single value.
```powershell
$obj = Get-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2"
$obj.Attributes["accountName"] = @("newaccountName")
```

When you have finished making value changes, you must call Commit() on the object to save the changes
```powershell
$obj.Commit()
```

To set the value of a multi-valued attribute you can pass in multiple values in the array
```powershell
$obj = Get-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2"
$obj.Attributes["mailAlternateAddresses"] = @("test@test.com", "test2@test.com")
$obj.Commit()
```

## Deleting an attribute 
An attribute can be deleted from an object by using the following command
```powershell
$obj = Get-AcmaObject -ID "efd7f79b-f0eb-42c0-ae3e-ea61ee57e0d5"
$obj.Attributes.Delete("accountName")
$obj.Commit()
```

## Adding a new object
An object can be created by specifying the object class you want to create
```powershell
$obj = Add-AcmaObject -ObjectClass person
```

## Deleting an object
An object can be deleted using the ID of the object, or an object itself
```powershell
Remove-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2"
```

```powershell
$obj = Get-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2"
Remove-AcmaObject $obj
```

If an object class allows objects to be undeleted, you can force the removal of an object using the `-ForceDelete` parameter
```powershell
Remove-AcmaObject -ID "153e0873-502c-4edf-9df1-1e39ae4889e2" -ForceDelete $true
```

## Viewing the attributes of an object
Once you have an object, you can use the write-host command to show all the attributes of an object

```powershell
Write-Host $obj
```

```
Object ID: c7d66109-1f60-4ad3-b305-8e1cc1356b2b
Object class: person
Deleted: No
Inherited update: No
accountBlocked: False
accountDisabled: False
accountExpired: False
accountName: smit0001
activationReady: False
activationSetupPending: False
activationToken: EoWazQVYrZUx99IiyZGag82UrdGtHf
activationTokenExpiry: 4/10/2014 8:19:46 PM
activeExpiryDate: 30/12/9999 1:00:00 PM
adminAttentionRequired: False
creationDate: 2/09/2014 5:33:45 AM
displayName: John Smith
domain: fim-dev1
mailFormat: 1
organizationalRelationships: OR0029
organizationalRelationships: OR0024
organizationalRelationships: OR0018
organizationalRelationships: OR0014
organizationalRelationships: OR0003
organizationalRelationships: OR0001
organizationalRelationships: OR0038
organizationalRelationships: OR0039
organizationalRelationships: OR0043
organizationalRelationships: OR0045
sendActivationMail: False
sendCreationNotificationMail: False
shadowContact: 3d7d48fe-a381-4c87-bbef-660777417808
unixLoginShell: /bin/bash
unixUid: 968779
```

## Overriding Execution Rules
A constructor usually has a set of execution rules that ensure it only runs under certain conditions. In some instances, you may wish to force a constructor to re-run without adhering to the conditions in the execution rule. Passing an array of constructor IDs to the Commit method causes those constructors to execute.
For example, you may add a new constructor to generate a new attribute for a set of existing objects. Creating a new constructor does not cause it to execute on existing objects, unless that object has an export update that triggers the rules on the constructor. The following powershell cmdlet allows you to force a constructor to run, ignoring its execution conditions.
Warning: The execution conditions are completely ignored when forcing a constructor to run. You must ensure that you only force the constructor to run on objects that meet your execution criteria
This example queries for all objects of the 'person' class whose firstName starts with 'rob'. It then calls Commit on those objects, and forces "My new constructor" and "My constructor group" to execute.
```powershell
$constructors = @("My constructor group", "My new constructor")
$classquery = New-AcmaQuery -Attribute "objectClass" -Operator Equals -Value "person"
$nameQuery = New-AcmaQuery -Attribute "firstName" -Operator StartsWith -Value "Rob"
$queryGroup = New-AcmaQueryGroup -Operator All -QueryObjects @($classQuery, $nameQuery)
$objects = Get-AcmaObjects $queryGroup
foreach($person in $objects) { $person.Commit($constructors) }
```

## Nested constructors inside groups
In order for a constructor contained inside a constructor group to execute, all the containing groups must have their execution rules overridden as well.
Consider the following constructor tree
```

- Account Name Generators

 * Account Name Type 1
 * Account Name Type 2
 * Account Name Types 3 and 4
  * Account Name Type 3
  * Account Name Type 4
```

In order to forced constructor "Account Name Type 4" to execute, both "Account Name Generators" and "Account Name Types 3 and 4" would all need to be overridden if they contain their own execution rules.
## Sending Events to Objects
PowerShell can be used to send events to objects when they are committed. Events sent by PowerShell are recognized by the 'event' rule, and therefore can be used to trigger constructors. When combined with queries, the ability to send events to objects that meet a specified criteria provides a very power script-based mechanism to update objects.
The following example will send the 'expiryDateLapsed' event to the specified object. 
```powershell
$obj = Get-AcmaObject C7D66109-1F60-4AD3-B305-8E1CC1356B2B
$obj.AddEvent("expiryDateLapsed")
$obj.Commit()
```

Alternatively it can be combined with a query. The following example finds all objects with an activeExpiryDate less than the current date, who currently do not have their account disabled.
```powershell
$query1 = New-AcmaQuery -Attribute activeExpiryDate -Operator LessThan -Value "%utcdate%"
$query2 = New-AcmaPresenceQuery -Attribute accountDisabled -Operator NotPresent
$query3 = New-AcmaQuery -Attribute accountDisabled -Operator Equals -Value false
$childGroup = New-AcmaQueryGroup -Operator Any @($query2, $query3)
$queryGroup = New-AcmaQueryGroup -Operator All @($query1, $childGroup)
$objs = Get-AcmaObjects $queryGroup
foreach($obj in $objs) { $obj.AddEvent("expiryDateLapsed"); $obj.Commit(); }
```

## Executing Unit Tests
Unit tests are executed using the Invoke-UnitTests cmdlet. Optionally, you can choose to save the results to a HTML file using the -HtmlReportFileName parameter.
```powershell
Invoke-AcmaUnitTests -HtmlReportFileName D:\madata\acma\report.html
```



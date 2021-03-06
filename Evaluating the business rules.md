# Evaluating the business rules
After completing the [[setup process | Setting up the lab environment]], you can perform the following tests to validate that the business rules have been executed correctly.
#### Rule 1: If a user has a first name and surname, then an accountName must be generated in the format of FNNNxxxx, where F is the first letter of the first name, NNN is the first three letters of the surname, and xxxx is a number used to make the username unique.
Execute the following command to ensure person1 has a username that meets the specified rules
```powershell
$person1.Attributes["accountName"]
```

Expected result
```
JSmi0001
```
#### Rule 2: If a user has only a surname, then an accountName must be generated in the format NNNNxxxx, where N is the first 4 letters of the surname, and xxxx is a number used to make the username unique.
Execute the following command to ensure person4 has a username that meets the specified rules
```powershell
$person4.Attributes["accountName"]
```

Expected result
```
Stew0001
```
#### Rule 3: All users must be assigned a unique unix UID, starting from the value 20000 and incrementing each time it is issued
Execute the following command to ensure that all users have a unique unix UID
```powershell
$person1.Attributes["unixUid"]
$person2.Attributes["unixUid"]
$person3.Attributes["unixUid"]
$person4.Attributes["unixUid"]
```

Expected result
```
20000
20001
20002
20003
```
#### Rule 4: Each user must have an email address in the format of firstName.surname@acma-demo.com, or surname@acma-demo.com if the user has no first name
Execute the following command to ensure that person 1 has a mail address of firstname.surname@acma-demo.com and person 4 has an email address of surname@acma-demo.com
```powershell
$person1.Attributes["mail"]
$person4.Attributes["mail"]
```

Expected result
```
John.Smith@acma-demo.com
Stewart@acma-demo.com
```
#### Rule 5: If the email address already exists, the format firstname.middlename.surname@acma-demo.com should be used, provided a middle name is present.
```powershell
$person3.Attributes["mail"]
```

Expected result
```
William.John.Keys@acma-demo.com
```
#### Rule 6: If that email address already exists or the user has no middle name, then a number can be appended to the name to make it unique.
```powershell
$person5.Attributes["mail"]
```

Expected result
```
William.Keys1@acma-demo.com
```
#### Rule 7: All users in the IT department must be automatically issued with an admin account alongside their normal user account
John Smith is the only user in the IT department, so we can validate he has an account by checking the hasAdminAccount attribute
```powershell
$person1.Attributes["hasAdminAccount"];
```

Expected result
```
True
```
#### Rule 8: A user's admin account must have the same `employeeNumber` and name attributes as the user
We can get the admin account object and see its properties
```powershell
$adminAccount = $person1.Attributes["adminAccount"][[0]];
$adminAccount.ToString();
```

Expected result
```
Object class: shadowAdminAccount
Deleted: No
Shadow link: adminAccount
Inherited update: No
employeeNumber: 1000
firstName: John
sn: Smith
```
#### Rule 9: A user's admin account must be the user's `accountName`, prefixed with `a-`
```powershell
$person1.Attributes["accountName"];
$adminAccount.Attributes["accountName"];
```

Expected result
```
Jsmi0001
a-Jsmi0001
```
#### Rule 10: Each user must have home folder created for them at the location `%temp%\accountName`
```powershell
Get-ChildItem $env:TEMP\acmausers | fl Name
```

Expected result
```
Name : JSmi0001
Name : Stew0001
Name : WKey0001
Name : WKey0002
Name : WKey0003
```
#### Rule 11: If the user's accountName changes, the home folder needs to be renamed
```powershell
$person2.Attributes["accountName"] = "Will0001";
$person2.Commit();
$person2.Attributes["homeFolderPath"];
Get-ChildItem $env:TEMP\acmausers | fl Name
```

Expected result
```
%temp%\acmausers\Will0001

Name : JSmi0001
Name : Stew0001
Name : Will0001
Name : WKey0002
Name : WKey0003
```
#### Rule 12: If the user is deleted, the home folder needs to be deleted
```powershell
Remove-AcmaObject $person5
Get-ChildItem $env:TEMP\acmausers | fl Name
```

Expected result
```
Name : JSmi0001
Name : Stew0001
Name : Will0001
Name : WKey0002
```
#### Rule 13: Each user must have an `orgUnitName` attribute that corresponds to the displayName of the organizational unit they are assigned to
```powershell
$orgUnit2.Attributes["displayName"]
$person1.Attributes["orgUnitName"]
```

Expected result
```
IT
IT
```
#### Rule 14: All people who supervise other staff members need to have their `directReports` attribute populated with the people who report to them
```powershell
foreach($report in $person1.Attributes["directReports"]) {$report.Attributes["accountName"]}
```

Expected result
```
Will0001
WKey0002
Stew0001
```

Previous step: [[Setting up the lab environment]]


# Lab Environment Setup
This demonstration environment allows you to setup a database and basic set of rules that can be used to experiment with ACMA functionality. The demonstration does not require any MAs to be set up in the synchronization service to function, although nothing prevents you from doing so.
The lab will demonstrate how to configure a database, schema, and create objects using PowerShell.
## Prerequisites

- Sysadmin rights on an SQL server to create the demo database
- The [[ACMA Editor | Installation]] component must be installed, and its associated prerequisites
- Copy the [demo ACMA configuration file](resources/demo ACMA configuration file) to C:\AcmaDemo

## Lab environment description
### Business rules
The lab environment implements the following business rules

- If a user has a first name and surname, then an accountName must be generated in the format of FNNNxxxx, where F is the first letter of the first name, NNN is the first three letters of the surname, and xxxx is a number used to make the username unique.
- If a user has only a surname, then an accountName must be generated in the format NNNNxxxx, where N is the first 4 letters of the surname, and xxxx is a number used to make the username unique.
- All users must be assigned a unique unix UID, starting from the value 20000 and incrementing each time it is issued
- Each user must have an email address in the format of firstName.surname@acma-demo.com, or surname@acma-demo.com if the user has no first name
- If the email address already exists, the format firstname.middlename.surname@acma-demo.com should be used, provided a middle name is present.
- If that email address already exists or the user has no middle name, then a number can be appended to the name to make it unique.
- All users in the IT department must be automatically issued with an admin account alongside their normal user account
- A user's admin account must have the same `employeeNumber` and name attributes as the user
- A user's admin account must be the user's `accountName`, prefixed with `a-`
- Each user must have home folder created for them at the location `%temp%\accountName`
- If the user's accountName changes, the home folder needs to be renamed
- If the user is deleted, the home folder needs to be deleted
- Each user must have an `orgUnitName` attribute that corresponds to the displayName of the organizational unit they are assigned to
- All people who supervise other staff members need to have their `directReports` attribute populated with the people who report to them

The [acma-demo.acmax](resources/acma-demo.acmax) comes pre-configured with these business rules. Download this file and place on the machine where you are running the demo from.
### Object classes
The lab environment will define three object classes. 

- A `person` object class
- An `orgUnit` object class
- An `adminAccount` object class, which is a shadow object class that inherits from person

### Attribute bindings
Along with the standard attribute bindings that you may find on a person object (`firstName`, `sn`, etc), to demonstrate the power of inheritance in ACMA, we will inherit the `displayName` of the referenced `orgUnit` assigned to the person, and present that on the person as `ouName`.
We will also create a reference back-link, so that the `directReports` attribute on a person, is populated by all the people that have a reference to that person as their `supervisor`.
The `adminAccount` shadow object will also automatically inherit the `employeeNumber` and name-related attribute directly from the parent person object.
### Constants
The lab setup creates two constants

|  Constant  |  Description  |
| --- | --- |
| homeFolderPathRoot | The base path where home folders will be created |
| mailSuffix | The domain-part suffix of the email address that will be generated for each person |
### Sequences
The lab setup creates two sequences in the database.

|  Sequence  |  Description  |
| --- | --- |
| unixUid | This is an incrementing value starting at 20,000 which gives each users a unique unix UID number |

Next step: [[Setting up the lab environment]]


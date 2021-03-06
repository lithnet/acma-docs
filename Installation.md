# Installation
The ACMA installer allows installation of the following separate components. 

- The Management Agent itself. This can only be installed on the FIM Synchronization Server.
- The ACMA Editor. This is the user interface used for creating ACMA rules. This can be installed on any 64-bit machine.
- The ACMA PowerShell module

## Installing the MA components
### Prerequisites

- A FIM Synchronization Server running FIM version 4.1.3441.0 or above
- Microsoft .NET framework 4.0 or above
- Windows Installer 4.5
- SQL Server 2012 or above
- The account performing the MA installation must have sysadmin rights on the target database. Only integrated windows authentication is supported by the MA.

### Installation details
The MA components are always installed into the Extensions folder of the FIM installation directory. The installer will prompt for a database server and database name. You must have sysadmin rights on the SQL server to complete this process. If the database already exists, it will be upgraded to the latest version of the database if required. If the database does not exist, it will be created.
### Important Notes

- If your SQL server is separate from the FIM sync server, you must run the installer from an elevated command prompt, or grant the sync server computer account rights to create a database on the remote server
- If you have additional copies of the ACMA database on the server, you must manually update the databases using the [[Update-AcmaDatabase]] PowerShell cmdlet.

## Installing the UI components.
### Prerequisites

- 64-bit operating system
- PowerShell 3.0 or above
- Microsoft .NET framework 4.0 or above
- Windows Installer 4.5
- Microsoft.MetaDirectoryServicesEx.dll copied from the FIM synchronization server (see note below)
- db_owner rights to the ACMA database for any account using the editor or PowerShell cmdlets

### Notes
The UI components can be installed on any 64-bit machine. However, if the editor components are not installed on the FIM Synchronization Server, the Microsoft.MetadirectoryServicesEx.dll file from the %ProgramFiles%\Microsoft Forefront Identity Manager\2010\Synchronization Service\Bin\Assemblies folder on the sync server must be copied into the %ProgramFiles%\Lithnet\ACMA Editor folder on the target machine, and placed in the same folder as the MSI during installation



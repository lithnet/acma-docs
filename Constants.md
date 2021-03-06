# Constants
ACMA is designed to support using the same configuration file across development, QA and production environments. However, each environment likely has settings that differ between these environments. Constants are stored in the database, meaning they can be used to store environment-specific settings, and can be referenced from the configuration file.

Constants are a simple mapping between a constant name and a value. To ensure the configuration file stays truly portable between these environments, values can be stored as constants in the database, and referenced from the configuration file.

A good example would be the name of the Active Directory domain in each environment. A constant _adDomain_ can be created that stores the NetBIOS name of the domain. In the configuration file, wherever the domain is required, it can be referenced using the _%adDomain%_ declaration.

Another example might be the user's home profile path. In production, users may have a path of _\\domain.local\users\accountName_, while in the development environment it may be _\\dev-domain.local\users\accountName_. Given an attribute called _accountName_ which stores the user name, creating a constant called _homeFolderPrefix_ and setting the value to _\\domain.local\users_ or _\\dev-domain.local\users_, the config file can simply contain a value declaration of _%homeFolderPrefix%\{accountName}_. The declaration will always expand to the correct value for that environment.

Constant names must be unique, and cannot be the same name as any of the [[built-in variables]] or [[sequences]].


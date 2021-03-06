# Unique value constructor
The unique value constructor is similar to the [[declarative value constructor]] in that it provides the capability to declare attribute values, but also provides a mechanism to ensure they are unique across the ACMA database.

The constructor allows the user to define 'friendly' declarations that will be used to try and generate a unique value, before falling back to a value that includes a number that will be used to force uniqueness.

Only single-valued attributes are supported by this constructor.
## Parameters
### Constructor ID
All constructors must have a ID that is unique across the configuration set. This includes across different class constructors. Any string value can be used using the characters A-Z, 0-9, and -.
### Disable constructor
This setting allows you to temporarily disable the constructor. Disabled constructors' execution conditions are never evaluated and the constructor never runs.
### Description
This field provides an opportunity to document what your constructor does. It is a free text field that can contain as much or as little information as you like
### Target attribute
The attribute that the constructor will modify the value on
### Modification type
This constructor always replaces the existing values on the attribute with the declared values.
### Ordered list of declarations to try
The constructor provides an opportunity to try a series of declarations to try and make the value unique using standard [[ACMA DL | acma declarative language]] syntax. A common example might be to try and build an email address using the middle name if the first name and surname combination is already taken. This parameter is optional.
```
{firstName}.{surname}@domain.com
{firstName}.{middleName}.{surname}@domain.com
```
### Unique fall-back value
If the ordered list of declarations did not result in a unique value, then the fall-back value (which is mandatory) will be used. This parameter must include either %o% or %n% within the declaration. This variable will be substituted by a number which will increment until a unique value is created. 

|  Variable  |  Description  |
| --- | --- |
| %n% | The constructor will always substitute a number in the declaration, starting from 1, regardless of the fact that the declaration may not need it to be unique |
| %o% | The constructor will only add a number in the declaration if the declaration needs it to be unique
From the email address example below, you may use %o% to the declaration.
```
{firstName}.{surname}%o%@domain.com
```
This will add a number to the end of the name part of the email address, only if the expanded value of {firstName}.{surname}@domain.com already exists in the database.

The %n% declaration comes in useful when you always want a number added to the value. This is commonly used for usernames with a defined naming convention.
```
{firstName>>GetFirstLetter}{surname>>GetFirst3Letters}%n%
```
This example (provided the two transforms indicated exist) will create a username with the first letter of the firstname, the first 3 letters of the surname, and a number. The number will start from '1' for the first user, and get incremented each a username with the same prefix is generated.
### Declarations
While elements of the declarations can contain [[transforms]], you can optionally specify a transform chain to apply to the expanded declaration before it is added to the attribute.
### Uniqueness attributes
The UVC requires you to specify what attributes should be searched when testing to see if the generated value is unique. The generated attribute must be unique across all the specified attributes. It is important to note that the uniqueness is validated against all objects in the database. You cannot limit the scope of the search to a specific object class.
A common use case for using multiple search attributes is validating generated email addresses against both a primary email address attribute, as well as a alternate or alias attribute.
The search attribute can be any combination of single-valued or multivalued attributes.
Indexing is an important consideration for your search attributes. Each uniqueness query performed by the constructor requires a database search. Without appropriately indexed attributes, export performance may suffer.
Note that the constructor's target attribute is not automatically considered for uniqueness. It must be added into the list manually if required.


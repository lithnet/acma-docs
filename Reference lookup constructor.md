# Reference lookup constructor
The reference lookup constructor (RLC) allows you to find objects in a database that match a specified criteria, and populate references to them on an attribute on the current object.
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
This constructor always replaces the existing values on the attribute. If not matches are found, any existing values are deleted.
### Multiple match action
You can configure how you want the constructor to handle a situation where multiple matches are found for the given search criteria. If the target is a single-valued attribute, you must choose an action to take. If the target is a multivalued attribute, you can store all the matches.

|  Parameter  |  Description  |
| --- | --- |
| Use all | All the matches found will be stored on the target attribute. This option is only available for multivalued attributes |
| Use first | Gets the first matching result and stores that on the target attribute |
| Use None | Deletes the attribute if more than one value is found |
| Error | Throws an error and aborts the current export operation |
### Lookup query
The lookup query node allows you to define the search criteria. It is a standard [[database query]] that can search multiple attributes across the various object classes. As with all database queries, attributes that are inherited on a particular object class cannot participate in a search, as they do not exist on the inheriting object within the database.


# Attribute delete constructor
The attribute delete constructor is the simplest of all constructors. It can only delete all values for a given attribute. If you are looking to delete a _specific value_ from an attribute, use a [[declarative value constructor]] instead
## Parameters
### Constructor ID
All constructors must have a ID that is unique across the configuration set. This includes across different class constructors. Any string value can be used using the characters A-Z, 0-9, and -.
### Disable constructor
This setting allows you to temporarily disable the constructor. Disabled constructors' execution conditions are never evaluated and the constructor never runs.
### Description
This field provides an opportunity to document what your constructor does. It is a free text field that can contain as much or as little information as you like
### Target attribute
The attribute that the constructor will delete all the values from
### Modification type
This constructor deletes all values present in an attribute


# Sequence allocator constructor
The sequence allocator constructor assigns the next value in a database [[sequence | sequences]] to the target attribute.
## Parameters
### Constructor ID
All constructors must have a ID that is unique across the configuration set. This includes across different class constructors. Any string value can be used using the characters A-Z, 0-9, and -.
### Disable constructor
This setting allows you to temporarily disable the constructor. Disabled constructors' execution conditions are never evaluated and the constructor never runs.
### Description
This field provides an opportunity to document what your constructor does. It is a free text field that can contain as much or as little information as you like
### Target attribute
The attribute that the constructor will modify the value on. Only single-valued integer attributes can be used as a target attribute.
### Modification type
This attribute always replaces any existing value on the target attribute.
### Sequence
The name of the database [[sequence | sequences]] to obtain the next value from


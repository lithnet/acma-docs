# Class Constructors
Each object class in ACMA can have a class constructor which defines

- Undelete parameters (for an object class marked as undeletable)
- Attribute constructors for the class
- Exit events

## Undelete parameters
When a class is marked as undeletable, the undelete parameters are used to search for an existing, deleted object in the database whenever a new object is exported from FIM. If the search parameters return a result, the existing object is undeleted, otherwise a new object is created. 
It is important to note that if the newly exported object from FIM contains attributes that conflict with those that are stored on the deleted object, the new attributes will overwrite any existing attributes.
The undelete parameters use the standard [[database query]] structure.

It is important to ensure that the attributes used in undelete searches are unique. If an undelete query returns more than one result, then an exception is thrown, and the export operation fails.

## Attribute Constructors
A class constructor has a series of [[attribute constructors]] that are used to build new values for attributes of that object class

## Exit events
[[Exit events]] are a powerful feature that allows you to trigger actions external to the object being exported. ACMA provides three types of exit events

- [[Internal exit events]]
- [[Command exit events]]
- [[Extension exit events]] 


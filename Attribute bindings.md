# Attribute Bindings
Attributes can be bound to an object class as either a simple or inherited binding. A simple binding allows an attribute to be read and written to in that object class.

Inherited attributes are a powerful feature that allows an attribute value to be inherited from another object. Inherited attributes are read-only on the object class they are bound to. The value itself is not stored on the inheriting object, and therefore cannot be used in database queries. The values can be used in rules and value declarations, and will be imported into FIM.

An common example of the use of an inherited attribute is when you want to populate a department name on a person object, based on a referenced organizational unit object. The _displayName_ of the object referenced by the _organizationalUnit_ attribute on the person, can be inherited as _departmentName_ on the person object.

If the inheritance source reference changes, or the inherited value itself, ACMA will automatically trigger an update to the inherited attribute.


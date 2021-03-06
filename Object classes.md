# Object Classes
An object class is a structural concept that is used to define a named group of bound [[attributes]]. The most simple object classes in ACMA has a defined name, and a set of attribute bindings, just the same as in the metaverse. However, ACMA allows for some additional capabilities above and beyond what FIM offers out-of-the-box.

## Undeletable Object Classes
If an object class is marked as undeletable, then when FIM sends a delete operation for the object to ACMA, it is marked in the database as deleted, and no longer imported back to FIM. The object and its attributes remains in the database.

These objects are still accessible in ACMA and can be used in searches by other objects.

If FIM sends an object add operation, and that object meets the undelete criteria specified in the [[class constructor | class constructors]], rather than creating a new object, ACMA will re-activate the deleted object, keeping all its existing attribute values in tact.

## Shadow Object Classes
[[Shadow Objects]] are objects that are created within ACMA, by deriving them from an existing object (the shadow parent). Shadow objects are created based on the value of a provisioning control attribute on the parent, and deleted either by the provisioning control attribute, or when the shadow parent is deleted. Shadow objects are presented to FIM in the same way as any other object


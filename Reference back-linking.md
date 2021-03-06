# Reference back-linking
ACMA provides the ability to provide automatic back-linking between two object classes and a reference value.

If object A references object B on the attribute objectAInstance, ACMA can automatically populate a reference to object B on object A's objectBInstance attribute.

Back-links are defined on the object class that has the _source_ reference attribute. The object class for the target must be specified (it can be the same object class), as well as the reference source and reference targets.

Once a relationship is defined, ACMA will automatically manage the back-linking process. It is important to note that management of back-links happens during an object's export. If there are existing objects in the database when a back-link is created, no automatic back-linking will take place for those objects, until the reference source attribute value is modified. 


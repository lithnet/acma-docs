# Shadow Objects
Shadow objects are a special object type within ACMA. While presented to FIM as an ordinary object class, they are in fact objects that are tightly coupled to, and inherit from another object.

There are some special attributes that are used in the control and creation of a shadow object. Firstly, the shadow object has a built-in attribute called _shadowParent_. This attribute contains the reference to the object that created the shadow object. The _shadowLink_ stores the name of the link, that defines the relationship between the shadow object and its parent. The _shadowParent_ and _shadowLink_ attributes are built-in and managed automatically by ACMA.

The shadow parent itself requires two user-defined attributes to be specified in a shadow link. The first is a provisioning control attribute. This must be a non-inherited Boolean attribute that is used to control whether the parent should create a shadow object. If the value is set to true, ACMA creates a new shadow object. If the value is set to false, then the shadow object is deleted.

The provisioning attribute is a normal attribute and can be set by any available means (e.g. constructor, export from FIM, PowerShell).

The second user-defined attribute is the shadow reference attribute. This must be a single-valued non-inherited reference attribute. When the provisioning attribute is set to true, and a shadow object is created, this attribute holds the reference to the shadow object. When the shadow object is deleted, this attribute value is deleted.

It is important to note that you cannot export an object 'add' of a shadow object to ACMA. The only way to create a shadow object is to set the provisioning attribute. However, FIM can export an object delete for a shadow object, and ACMA will delete the shadow object, and set the provisioning control attribute to false.

Shadow objects cannot exist without their parent. If the parent is deleted, then the shadow object is automatically deleted as well.

## Defining a shadow object relationship
This common use of this type of object is for the creation of a secondary account for a user. This might be for a high-privilege administrator account in a system. An attribute called _hasAdminAccount_ could be bound to the person and used as the provisioning attribute, while the _adminAccount_ attribute is used to store the reference to the shadow object. 

- Create a new object class called _person_
- Create a Boolean attribute called _hasAdminAccount_
- Create a single-valued reference attribute called _adminAccount_
- Bind _hasAdminAccount_ and _adminAccount_ to person
- Create a new shadow object class called _shadowAccount_ that inherits from _person_
- Create a shadow object link with the name _adminLink_, specifying _hasAdminAccount_ as the provisioning control attribute and _adminAccount_ as the reference attribute

Whenever the _hasAdminAccount_ attribute is set to true, a new object will be created. You can define constructors for the shadow object class and use it just as you would any other object class.




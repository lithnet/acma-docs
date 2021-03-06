# Attributes
## Data Types
Attributes in ACMA share similar data type structures to the FIM metaverse. The following attribute types are supported.


|  *Attribute Type*  |  *Length*  |  *SQL datatype*  |  *Presented to MV as*  |
| --- | --- | --- | --- |
| String (indexable) | 400 characters | nvarchar(400) | String (indexable) |
| String | 2GB | nvarchar(MAX) | String |
| Integer | 64 bit | bigint | Integer |
| Boolean | 1 bit | bit | Boolean |
| Reference |  16 bytes | uniqueidentifier | Reference |
| DateTime | 7 bytes | datetime2(3) | String (indexable)* |
*As the FIM metaverse doesn't have a native DateTime data type, these attributes are imported into FIM as an ISO 8601 date time string, in the same way the FIM service does. In ACMA these values are stored as native dates, and can be compared and modified as natural date times.

As with the metaverse, all attributes can be multi-valued, apart from those with the Boolean data type.

## Operations
Attributes can be configured for the following types of operations

|  *Operation*  |  *Description*  |
| --- | --- |
| Export from FIM | The attribute supports being exported from FIM to ACMA only |
| Import to FIM | The attribute can be imported to FIM only |
| Import/Export | The attribute can be both imported to and exported from FIM |
| Internal | The attribute is not visible to FIM, but is usable in ACMA |
| Temporary | The attribute is not visible to FIM, and is not stored in the database. It is usable only within a single export session of an object. These attributes are useful for temporarily storing data, similar to how one might use a variable in code |

Operations set on the attribute apply to all object classes that use the attribute. You cannot have different operation types for the same attribute bound to different object classes.

{anchor:indexing}
## Indexing
Indexing attributes allows ACMA to efficiently search for values when used in lookup queries, uniqueness checks, and event processing. Without appropriate indexing, searching the database can become very slow. However, indexing an attribute increases the cost of writes to the database, so the appropriate balance between the two needs to be found.

As a general guideline, if the attribute is not being searched on, or the searches are likely to be very infrequent, then do not index the attribute. Otherwise, an index should be applied.

The topic of database performance and tuning is a complex one. As each environment is different, there are no hard and fast rules about what should or should not be done. Your local DBA can provide profiling and tuning advice specific to your environment.

## Built-in attributes
There are certain built-in attributes in ACMA that cannot be modified, but can be read and used in rules and value declarations.

|  *Attribute name*  |  *Description*  |
| --- | --- |
| objectId | The unique ID assigned to an object |
| deleted | Stores the time, in .NET ticks that an object was deleted. If an object is deleted this value is non-zero. This only applies to objects that have classes marked as undeletable |
| shadowParent | The parent object of a shadow object |
| shadowLink | The name of the link object that defines a shadow object relationship |
| objectClass | The name of the class of the object |



# Database queries
ACMA provides the ability to search for objects in the database. These queries are used in the [[reference lookup constructor]], [[exit events]], [[undelete parameters | class constructors#undeleteparameters]], and [[pre-operation events]].

## Query groups
All query structures start with a top-level query group. A query group allows you to set the type of operator to apply in order to find the objects in the database.

|  Operator  |  Description  |
| --- | --- |
| Any | Any of the conditions in the group must be satisfied for a match to be made |
| All | All of the conditions in the group must be satisfied for a match to be made |
| One | Only one of the conditions in the group can be satisfied for a match to be made |
| None | None of the conditions in a group can be satisfied for a match to be made |

Query groups can contain nested query groups, whose operators are considered independently from the parent group.

## Value queries
A value query specifies exactly what type of comparison to perform on the target attribute. It is important to note that the value query is executed on the database directly. When an object is being exported, it's attribute changes exist in memory, and not in the database. Only once the export operation is completed are the changes written to the database. Searches against attributes on an object that has not yet been committed may not return the correct results.
### Parameters

|  Parameter  |  Description  |
| --- | --- |
| Search attribute | The attribute search against in the database |
| Operator | The type of comparison to perform. See the _value query operator_ section below for more details |
| Value | A standard [[ACMA DL | acma declarative language]] declaration |
| Transforms | The transforms to apply to the result of the value declaration |

### Operators
#### All data types

- Is present
- Is not present

#### String

- Equals
- Does not equal
- Contains
- Does not contain
- Starts with
- Ends with

#### Boolean

- Equals
- Does not equal

#### Reference

- Equals
- Does not equal
- Is present
- Is not present

#### Integer

- Equals
- Does not equal
- Is greater than
- Is greater than or equal to
- Is less than
- Is less than or equal to
- Is present
- Is not present

#### DateTime

- Equals
- Does not equal
- Is greater than
- Is greater than or equal to
- Is less than
- Is less than or equal to
- Is present
- Is not present

### Indexing
It is important to consider your attribute indexing strategy when designing searches. A frequently performed search on an unindexed attribute will result in slow searches and possible undesirable export performance. However having a large number of indexed attributes can slow down writes to the database. Please see the [[indexing | attributes#indexing]] section of the attributes page for more information.
### Object classes
As query objects are not constrained to a specific object class, the drop down list for the target attribute will always include all attributes. It is up to the user to ensure that the attribute they are searching for exists on the class of object being searched. If the attribute doesn't exist on an object class, an error will not be thrown, but search results may be incorrect. 

It is advisable to include a value query for the _objectClass_ attribute in your query group to constrain the search to just the object class you are interested in.


# Declarative value constructor
The declarative value constructor (DVC) is likely the constructor you will use the most within your deployment. It provides a simple yet powerful way to declare the values of an attribute using easy to read [[ACMA DL | acma declarative language]].
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
The modification type field controls the behavior of the constructor. There are some slight differences in the way these options act on the attribute depending if it is a multivalued or single-valued attribute.

|  Value  |  MV behavior  |  SV behavior  |
| --- | --- | --- |
| Add | Adds the declared values to the attribute | Adds the value if it doesn't exit, and replaces it if it does exist |
| Replace | Replaces all existing values on the attribute with the declared values | Adds the value if it doesn't exit, and replaces it if it does exist |
| Delete | Deletes the declared values from the attribute if they exist | Deletes the declared value from the attribute if it exists |
| Conditional | Performs an add operation if the presence conditions are met, and a delete if they are not | Performs an add operation if the presence conditions are met, and a delete if they are not |

It is important to note that the _delete_ option only deletes a value from the attribute that is present in the declaration. If the declared value is not found on the attribute, the attribute remains unchanged.

When the modification type is set to _conditional_, a _presence conditions_ element is added to the declarative constructor (under the _execution rules_ node) in the tree view. Using standard [[rules]], you can define the conditions under which the constructor should add the declared values. If those conditions are not met, and the attribute contains one of the declared values, then it will be removed.

The constructor's execution rules must still be met for the constructor to evaluate the presence conditions.

### Declarations
The DVC supports a single declaration for single-valued attributes, and multiple declarations for multivalued attributes. When you select a multivalued attribute, additional rows will be added to the declarations grid. 
While elements of the declaration can contain [[transforms]], you can optionally specify a transform chain to apply to the expanded declaration before it is added to the attribute.



# Value comparison rule
The value comparison rule compares the value of an attribute with the value specified in the rule. The types of comparisons available depend on the type of the attribute being evaluated. The rule can also evaluate an object that is referenced by the object under evaluation.

## Parameters
|  Value source  |  Specifies that the value comparison is perform on the current object, or an attribute referenced by the current object  |
| --- | --- |
| Attribute | The attribute to evaluate |
| Group operator | When the target is a multivalued attribute, the group operator is used to determine how to evaluate the rule. The group operator can specify that any, all, none, or one of the attribute values must match the value provided in the rule |
| Value operator | The type of comparison to perform |
| Value | The value to use in the comparison. This can be any valid [[ACMA DL | acma declarative language]] string |
| Transforms | The transform chain to apply to the expanded value from the _value_ parameter |
The value declaration provided will first be expanded, and then transformed, before being compared to value on the object.

## Allowed comparison operators
### String

- Equals
- Does not equal
- Contains
- Does not contain
- Starts with
- Ends with

### Integer

- Equals
- Does not equal
- Is greater than
- Is greater than or equal to
- Is less than
- Is less than or equal to

### Boolean

- Equals
- Does not equal

### Reference

- Equals
- Does not equal

### DateTime

- Equals
- Does not equal
- Is greater than
- Is greater than or equal to
- Is less than
- Is less than or equal to

### Binary

- Equals
- Does not equal



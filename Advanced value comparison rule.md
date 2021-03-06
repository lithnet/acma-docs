# Advanced Value Comparison Rule
An advanced value comparison rule compares the output of two value declarations defined using [[ACMA DL | acma declarative language]]. This type of rule can evaluate complex scenarios involving multiple attributes and transforms.

As ACMA does not know in advance what the resulting type of the value declarations will be, you must define the comparison type to use in the evaluation. If the value declarations expand to a data type that does not match the value specified in the _compare as_ parameter, an error will be raised and the operation will fail 

## Parameters
|  Name  |  Description  |
| --- | --- |
| Group operator | If the first value parameter is expanded and returns a multivalued response, the group operator is used to determine how to evaluate the rule. The group operator can specify that any, all, none, or one of the first values must match the second value provided in the rule |
| First value | The first value to use in the comparison. This can be any valid [[ACMA DL | acma declarative language]] string |
| Operator | The type of comparison to perform. This is dependent on the _compare as_ parameter |
| Second value | The second value to use in the comparison. This can be any valid [[ACMA DL | acma declarative language]] string |
| Transforms | The transform chain to apply to the expanded value from the _value_ parameters |
| Compare as | Specifies the type of data that will be compared. |
The value declarations provided will first be expanded, and then have any transformed applied, before being compared to each other.

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


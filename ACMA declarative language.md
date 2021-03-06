# ACMA Declarative Language (ACMA DL)
ACMA uses a declarative language syntax that allows values to be derived from existing [[attributes]], [[constants]], and [[built-in variables]]

## Declaring attributes
Attributes can be declared using braces (curly brackets). _Simple declarations_, as shown below can be  used for any attribute type, including multi-valued attributes
- `{accountName}`
- `{locations}`

_Complex declarations_ can include multiple attributes, as well as other text, provided that the attributes used in the declaration are singled valued. A multi-valued attribute must be the only element in a value declaration.
Given a single-valued attribute called _accountName_ and a multi-valued attribute called _officeLocations_, the following examples apply.

Supported

- `\\\\domain.local\\users\\{accountName}`
- `{officeLocations}`

Not supported

- `Melbourne-{officeLocations}`

## Optional attribute declarations
Parts of a declaration can be dropped if an attribute is not present. Consider the following declaration to build an email address

- `{firstName}.{middleName}.{surname}@test.com`

If the middleName attribute was not present, the declaration would incorrectly expand to *Bob..Smith@test.com*.
To avoid having to have multiple constructors with different declarations, square brackets (`[[ ]]`) can be used to denote optional text in a declaration. The text inside the square brackets will only be included in the attribute contained in the square brackets has a value. If we place the declaration for `{middleName}` along with the period inside the square brackets, the value will expand correctly.

- `{firstName}.[[{middleName}.]]{surname}@test.com`

This will expand to *Bob.Smith@test.com* if no middle name is present, and *Bob.John.Smith@test.com* if the middle name is present.

## Built-in variables, constants, and sequences
[[Built-in variables]], [[constants]] and [[sequences]] are all accessed using the % declaration. As these are all single valued, they can be used in complex declarations.
- `%utcdate%`
- `%unixUid%`

## Transforms
[[Transforms]] can be inserted into declarations to modify any attribute or variable according to the rules of the transform. Transforms can also be chained together. Note that it is possible to use a multi-valued attribute in a complex declaration if a multi-valued to single valued transform is used.
- `{accountName>>ToLowerCase}`
- `Melbourne-{officeLocations>>GetFirstValue}`
- `%utcdate>>Add6Months%`
- `%homeFolderGroup>>Format4DigitNumber%`
- `{surname>>GetFirstCharacter>>ToLower}`

## Type Coercion
ACMA provides an intelligent and automatic type conversion system. When a mismatched data type is found, ACMA will attempt to coerce the value into the target data type using the [[type coercion model]].

## Escape characters
The following characters in ACMA DL are reserved, and need to be escaped with a backslash when used as literals
` \ { } % [[ ]] `

- `\\\\domain.local\\users\\{accountName} -> \\domian.local\users\jsmith`
- `Office Manager \[[Melbourne\]] -> Office Manager [[Melbourne]]`

## Auto-complete
Where it is clear to the ACMA editor what object class is in context, only the attributes that bound to that object class are shown in the auto-complete list. Otherwise, all attributes are shown in the list, and it is up to the user to ensure that the specified attribute is available on the object class.



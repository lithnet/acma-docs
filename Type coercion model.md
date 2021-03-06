# Type Coercion
ACMA provides an intelligent and automatic type conversion system. When a mismatched data type is found, ACMA will attempt to coerce the value into the target data type using the model shown below.


|  Source Type  |  String  |  Integer  |  Binary  |  Boolean  |  DateTime  |  Reference  |
| --- | --- | --- | --- | --- | --- | --- |
| Target Type |
| String | String | String | Base-64 encoded string | True/False string | ISO 8601 date string | GUID string |
| Integer | Cast to integer if it is a number | Integer | 0 = false, 1 = true | not supported | not supported | not supported |
| Binary | Cast to binary if base64 string | not supported | Binary | not supported | not supported | not supported |
| Boolean | Cast to Boolean if value is true/false/0/1 | Cast to Boolean if value is 0 or 1 | not supported | Boolean | not supported | not supported |
| DateTime | Cast to DateTime if value is a ISO 8601 string | not supported | not supported | not supported | DateTime | not supported |
| Reference | Cast to GUID if value is a string representation of a GUID | not supported | not supported | not supported | not supported | Reference |


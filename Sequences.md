# Sequences
Sequences are an SQL 2012 feature that allows you to define an automatically incrementing number. Once a number is issued, SQL automatically increments to the next number in the sequence. 

ACMA provides the ability to define these sequences directly in the editor
## Settings

| *Name* | The name of the sequence, which is used in value declarations | 
|  *Start value*  |  The number to start the sequence from  |
| --- | --- |
| *Increment by* | The number to increment by each time the sequence is called |
| *Min value* | The minimum value that can be issued |
| *Max value* | The maximum value that can be issued |
| *Cycle* | Indicates if the sequence should start again from the minimum value whenever the maximum value is reached |
## Using sequences
Sequences are used in [[value declarations | ACMA Declarative Language]] using the %sequenceName% notation.
## Examples
Sequences can be used to assign things like unix UID numbers, perhaps starting at 20,000 and incrementing for each assigned value. 

Cycled sequences can be used to stripe users across a set of home folder groups. By setting a minimum value of 1 and a maximum of 5, each user would be assigned a value of 1-5. The sequence returns back to the start after issuing the 5th value.

Sequence names must be unique, and cannot be the same name as any of the [[built-in variables]] or [[constants]].


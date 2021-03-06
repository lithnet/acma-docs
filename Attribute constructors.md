# Attribute Constructors
Attribute constructors are used within ACMA to create, update, and delete attribute values. 

## Execution conditions
Each constructor can have one or more [[rules]] that determine if it should execute or not. A constructor whose conditions are met is allowed to execute, while those that don't are skipped. While execution conditions are optional, careful thought should be given to using a constructor without execution rules. These constructors may execute unconditionally every time an object is exported and modify the attribute values unintentionally. However, execution conditions on [[constructor groups]] may be enough to stop this from happening. Careful planning, design, and testing of constructors, groups and their execution conditions is required.

## Constructor types 
There are 5 types of attribute constructors

- [[Declarative value constructor]]
- [[Unique value constructor]]
- [[Attribute delete constructor]]
- [[Reference lookup constructor]]
- [[Sequence allocator constructor]]

## Constructor groups
Attribute constructors can be placed into [[constructor groups]]. Constructor groups can have their own execution conditions on them, which prevent all its child constructors from executing if its conditions are not met. 


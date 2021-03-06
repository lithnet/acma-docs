# Constructor groups
Attribute constructor groups provide two main functions and are an important design consideration for planning your business rules.

## Constructor groups without execution conditions
Constructor groups without any execution conditions of their own provide a way to group related constructors together to make the UI easier to navigate. The group simply exists as a mechanism to hide and show constructors in the UI, and does not plat a part in the logical execution of constructors within them.

## Constructor groups with execution conditions
Constructor groups with execution conditions prevent any constructors within the group from executing unless the group's conditions are met first. These constructors are very useful for allowing certain constructors to execute when a related set of conditions must be met.

Consider the following example:
```
ConstructorGroup1

- Execution Conditions
- On object add

 - AttributeConstructor1
   * Execution Conditions
   ** AttributeChangeRule
 - AttributeConstructor2
```

This very simple example shows a constructor group with a single [[object change rule]] for an object add. The constructors within the group would only be evaluated for execution if the object change type is 'add'. Of course those constructors can have their own execution conditions on them that will be evaluated independently, but the group's conditions save processing time by bypassing the entire group for object updates and deletes.

In very large environments with many rules, the use of execution conditions on groups and constructors is extremely important in ensuring ACMA can perform the class construction as efficiently as possible. Careful consideration, planning, and testing needs to go into the design of constructor groups and their execution conditions.

## Execution mode
By default, constructors trigger the execution of all child objects within it if its own execution conditions are met. Groups however can be set to _exit after first execution_. When set to this mode, once one of its child object passes its own conditions and executes, the group will stop processing, and not execute the remaining children in the group. This is commonly used when you have multiple constructors that set different values for the same attribute under different conditions. 

## Disabling a constructor group
If a constructor group is disabled, it will never execute the child objects within it. This can be useful for testing and diagnostic purposes.


# Rules
ACMA provides a base set of rules that can be used on attribute constructors, constructor groups, events. 
The rules are broken up into two types.

## Event-based rules
Event-based are very fast and efficient rules that look at the in-memory changes on an object. They are the lowest-cost rules to evaluate, and as such ACMA will evaluate event-based rules within a group first.
- [[Object change rule]]
- [[Attribute change rule]]
- [[Event rule]]

## Comparison-based rules
Comparison-based rules compare values on an object in the database against the parameters defined in the rule.
- [[Attribute presence rule]]
- [[Value comparison rule]]
- [[Advanced value comparison rule]]

## Rule groups
[[Rule groups]] are used to do more complex evaluations of an object. Rule groups can contain any number of rules, as well as child rule groups. They allow a conditional evaluation to take place, specifying that all, any, one, or none of their child rules and rule groups must pass evaluation for the group itself to pass.

## Rule debugging
At times, you may need to debug your rules to find out why a constructor or event isn't triggering. By default, ACMA doesn't log the details of rules comparisons, but debugging can be turned on by a registry setting. Please note that this setting will generate very large log files, so ensure you have plenty of disk space, and be sure to turn it back off when you have completed your investigation.

To turn on advanced rule debugging, create or set the value of the following registry value as shown below
```
HKEY_LOCAL_MACHINE\Software\Lithnet\ACMA
Key Name: Rule Debugging
Type: DWORD
Value: 1
```

To turn off advanced rule debugging, delete or set the value of the following registry value as shown below
```
HKEY_LOCAL_MACHINE\Software\Lithnet\ACMA
Value Name: Rule Debugging
Type: DWORD
Value: 0
```



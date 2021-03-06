# Rule groups
Rule groups are used to perform evaluation of multiple rules or other rule groups. Rule groups are hierarchical and evaluated from the top-down.

A group has a success criteria that defines how the group considers itself to have successfully passed evaluation.

### "Any" groups
A group with a success criteria of 'any' passes when any of its child rules or rule groups passes
### "All" groups
A group with a success criteria of 'all' passes only when all of its child rules and rule groups passes
### "One" groups
A group with a success criteria of 'one' passes only when one, and only one of its child rules or rule groups passes. If more than one child objects passes, or none of them pass, the group fails evaluation.
### "None" groups
A group with a success criteria of 'none' passes only when none of its child rules or rule groups passes.

It is important to note that a group's success criteria only applies to its immediate child objects. Consider the following scenario

```
Group 1 (All)

- Rule 1
- Rule 2
- Group 2 (Any)
- - Rule 3
- - Rule 4

```

If in the scenario above, rules 1, 2, and 3 pass, but 4 does not, group 1 will still evaluate as successful, as group 2 had an _any_ condition, and one of its rules did succeed.

If only rule 1 and 2 passed, then group 1 would have failed, as group 2 did not pass its own evaluation criteria.

## Shortcut evaluation
ACMA uses shortcut evaluation, and may not evaluate every rule in the chain if it knows the group is going to pass or fail. Consider the following scenario.

```
Group 1 (All)
 - Rule 1
 - Rule 2
```

If rule 1 fails, processing stops and group 1 reports that it failed evaluation. Rule 2 is never evaluated, as regardless of its outcome, the group has already failed its own criteria for success.

Another example is with an _any_ group
```
Group 1 (Any)
 - Rule 1
 - Rule 2
```

If rule 1 succeeds, rule 2 never gets evaluated, because the group has already met the conditions required for it to be successful.


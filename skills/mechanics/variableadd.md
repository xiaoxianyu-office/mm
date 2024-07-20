## Description
Adds an amount to a [variable](/skills/variables) on the specified
scope. Only works with numeric variable types.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| var       | name, key | The scope and name of the variable                                   |         |
| amount    | a, value, val, v  | The amount to add                                            | 1       |


## Examples
```yaml
  Skills:
  - variableadd{var=skill.testVar;amount=1} ~onInteract
```


## Aliases
- [x] addVariable
- [x] varAdd
- [x] addVar
- [x] incrementVariable
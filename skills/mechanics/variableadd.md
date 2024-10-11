## Description
Adds an amount to a [variable](/skills/variables) on the specified
scope. Only works with numeric variable types.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a, value, val, v  | The amount to add                                            | 1       |
> This mechanic inherits every *inheritable* attribute of the [SetVariable](skills/mechanics/setvariable) mechanic


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
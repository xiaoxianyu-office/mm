## Description
Subtracts an amount to a [variable](/skills/variables) on the specified
scope. Only works with numeric variable types.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a, value, val, v  | The amount to subtract                                       | 0       |
> This mechanic inherits every *inheritable* attribute of the [SetVariable](skills/mechanics/setvariable) mechanic


## Examples
```yaml
  Skills:
  - variablesubtract{var=skill.testVar;amount=1} ~onInteract
```


## Aliases
- [x] variableSub
- [x] subtractVariable
- [x] subVar
- [x] reduceVariable


<!--TAGS-->
<!--tag:Variable-->

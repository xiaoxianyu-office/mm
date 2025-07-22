## Description
Subtracts an amount to a [variable](/skills/variables) on the specified
scope.

> This mechanic can
> - subtract numeric values to Integer, Float and Double variables
> - remove a value from a Set variables
> - remove a value from a List variables by specifying its index (starts at 0)
> - remove a key-value pair from Map variables by specifying their key
> 
> [More Info Here](/Skills/Variables#special-variable-types)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a, value, val, v  | The value to subtract                                       | 0       |
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
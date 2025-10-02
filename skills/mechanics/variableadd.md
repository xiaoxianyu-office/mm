## Description
Adds an amount to a [variable](/skills/variables) on the specified
scope.

> This mechanic has different behavior based on the variable type. [More Info Here](/Skills/Variables#variable-types-behavior)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a, value, val, v  | The value to add                                             | 0       |
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


<!--TAGS-->
<!--tag:Variable-->
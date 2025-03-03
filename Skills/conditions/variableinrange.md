## Description
Checks if the given numeric variable is within a certain range.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| variable  | name, n, var, key, k | Variable to match, optionally prefixed by a scope         |         |
| value     | val, v, range, r     | A number range to match                                   |         | 
| scope     | s         | The [scope](/Skills/Variables#variable-scopes) of the variable, e.g. where the variable is located                                                                            |<!--type:VariableScope-->|


## Examples

```yaml
  Conditions:
  - variableInRange{var=caster.Cooldown;value=<0.01} cancel
  Skills:
  - setvariable{var=caster.Cooldown;type=float;value="10"}
  - message{m="&7Cooldown over!"}
```


## Aliases
- [x] varinrange
- [x] varrange
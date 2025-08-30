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
ShootCheck:
  Cooldown: 0
  Conditions:
  - variableInRange{var=caster.shootsLeft;value=>0} castInstead ShootThemUp
  Skills:
  - message{m="&7Reloading..."} @self
  - delay 0
  - setskillcooldown{skill=ShootCheck;seconds=2} @self
  - delay 20
  - setvariable{var=caster.shootsLeft;value=10} @self
  - message{m="&7Reloaded!"} @self
```


## Aliases
- [x] varinrange
- [x] varrange
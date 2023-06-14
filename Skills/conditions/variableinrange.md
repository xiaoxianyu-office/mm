## Description
Checks if the given numeric variable is within a certain range.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| variable  | name, n, var, key, k | Variable to match                                         |         |
| value     | val, v, range, r     | A number range to match                                   |         | 


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
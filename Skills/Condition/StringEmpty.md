## Description
Checks if the provided string is empty


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| value     | val, v, string, s | The string to check                                          |         |


## Example
```yaml
  Conditions:
  - stringEmpty{value=<caster.var.examplevariable>}
```
> Checks if the value of the <caster.var.examplevariable> placeholder is an empty string


## Aliases
- [x] isEmpty
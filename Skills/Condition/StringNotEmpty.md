## Description
Checks if the provided string is not empty


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| value     | val, v, string, s | The string to check                                          |         |


## Example
```yaml
  Conditions:
  - stringNotEmpty{value=<caster.var.examplevariable>}
```
> Checks if the value of the <caster.var.examplevariable> placeholder is *not* an empty string


## Aliases
- [x] notEmpty
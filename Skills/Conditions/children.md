## Description
Checks how many children the caster has.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of children to check for. Can accept ranged values.       | 1       |



## Examples
```yaml
  Conditions:
  - children{a=1} true
```
```yaml
  Conditions:
  - children{a=>2} true
```
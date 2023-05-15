## Description
Whether the distance between the caster and target is within the given range.  
Can be a single number, a ranged value (20to40), or >10 <5, etc.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  |   d       | The distance to match                                                |         |


## Examples
```yaml
  TargetConditions:
  - distance{d=<2}
```
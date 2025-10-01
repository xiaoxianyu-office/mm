## Description
Checks the difference in x value between the target entity and the caster.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| difference| diff, d   | The x difference to check                                            |         |


## Examples
```yaml
  TargetConditions:
  - xDiff{diff=>5} true
```
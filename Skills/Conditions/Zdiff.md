## Description
Checks the difference in z value between the target entity and the caster.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| difference| diff, d   | The z difference to check                                            |         |


## Examples
```yaml
  TargetConditions:
  - zDiff{diff=>5} true
```
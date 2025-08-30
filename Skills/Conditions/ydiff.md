## Description
Checks the difference in y value (height) between the target entity and the caster.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| difference| diff, d   | The y difference to check                                            |         |


## Examples
```yaml
  TargetConditions:
  - yDiff{diff=>5} true
```
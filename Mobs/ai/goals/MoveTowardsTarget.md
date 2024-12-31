## Description
Causes the mob to move towards its target


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed     | s         | The speed of the movement                                            | 0.9     |
| maxrange  | range, r  | The max range in which to engage this behavior                       | 32.0    |


## Examples
```yaml
  AIGoalSelectors:
  - clear
  - moveTowardsTarget
```
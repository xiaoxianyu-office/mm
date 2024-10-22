## Description
Causes the mob to look at its target


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| maxrange  | range, r  | The maximum range in which the target must be in order for this goal to be effective   |    32     |
| speed     | s         | The speed of the motion                                              | 0.9     |
| onlyhorizontal | horizontal, h | Whether the mob will not change pitch when looking at the target | false |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - lookAtTarget{r=12;h=true}
```
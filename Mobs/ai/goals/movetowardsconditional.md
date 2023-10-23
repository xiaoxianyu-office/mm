## Description
Causes the mob to move towards targets based on provided conditions.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance | d        | The speed to move towards targets |    0.9    |
| maxrange | range,r        | The max range of the target |    32    |
| conditions |         | The conditions to use |        |

## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - movetowardsconditional{d=2;r=16;conditions=[ - inlineofsight true ]}
```
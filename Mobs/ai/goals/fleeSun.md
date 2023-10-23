## Description
Causes the mob to flee from the sun and hide in shade.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed | s        | The speed at which to move towards shade |    1    |

## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - fleesun{s=2}
```
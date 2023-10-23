## Description
Causes the mob to find a path through a village.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed | s        | The speed at which to move |    0.6    |

## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - movethroughvillage{s=2}
```
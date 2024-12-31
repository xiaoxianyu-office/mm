## Description
Causes the mob to move towards lava.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed | s        | The speed at which to move |    0.9    |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - movetolava{s=2}
```


## Aliases
- [x] gotolava
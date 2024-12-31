## Description
Causes the mob to leap towards its target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed | s        | The speed at which to leap at the target |    1.2    |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - leapattarget{s=4}
```


## Aliases
- [x] leaptowardstarget
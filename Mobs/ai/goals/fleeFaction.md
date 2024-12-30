## Description
Causes the mob to flee from a specific faction.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance | d        | The distance for targets to be from the mob itself |    4    |
| speed | s        | The speed at which to flee |    1.2    |
| safespeed | ss        | The speed at which to flee once a safe distance (50 blocks) away |    1    |
| faction | f        | The faction to flee from |        |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - fleefaction{distance=5;speed=2;safespeed=2;faction=somefaction}
```


## Aliases
- [x] runfromfaction
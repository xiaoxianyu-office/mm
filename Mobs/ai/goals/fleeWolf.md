## Description
Causes the mob to flee from wolves.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance | d        | The distance for wolves to be from the mob itself |    6    |
| speed | s        | The speed at which to flee |    1.2    |
| safespeed | ss        | The speed at which to flee once a safe distance (50 blocks) away |    1    |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - fleewolf{d=10;s=2;ss=1}
```


## Aliases
- [x] runfromwolves
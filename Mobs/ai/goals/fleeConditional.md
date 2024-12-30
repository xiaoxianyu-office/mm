## Description
\*\***This is a Premium only feature**\*\*<br>
Causes the mob to flee based on provided conditions.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance | d        | The distance for mobs to be from the mob itself |    4    |
| speed | s        | The speed at which to flee |    1.2    |
| safespeed | ss        | The speed at which to flee once a safe distance (50 blocks) away |    1    |
| conditions | c, cond, fleeconditions | The conditions to use |        |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - fleeConditional{distance=5;speed=2;safespeed=2;conditions=[ - inlineofsight true ]}
```


## Aliases
- [x] fleeif
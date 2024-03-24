## Description
A basic ranged attack that ranged entities can use.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed     | s         | Movement speed modifier                                              |    1    |
| attackspeedmax | smax     | The maximum interval per shot (in ticks)                         |   60    |
| attackspeedmin | amin     | The minimum interval per shot (in ticks)                         |   20    |
| attackradius | radius, r | The attack radius of this ai goal                                 |   15    |


## Examples
```yaml
ExampleMob:
  Type: Skeleton
  AIGoalSelectors:
  - clear
  - rangedAttack{speed=1;smax=60;amin=20;radius=15}
```


## Aliases
- [x] rangedAttack
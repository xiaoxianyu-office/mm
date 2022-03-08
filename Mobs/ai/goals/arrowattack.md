Goal: rangedAttack
--------------

*Aliases*: arrowAttack

A basic ranged attack that ranged entities can use.

### Attributes

| Attribute      | Aliases  | Description                        | Default |
|----------------|----------|------------------------------------|:-------:|
| speed          | s        | Movement speed modifier            |    1    |
| attackspeedmax | smax     | The maximum attack speed           |   60    |
| attackspeedmin | amin     | The minimum attack speed           |   20    |
| attackradius   | radius,r | The attack radius of this ai goal. |   15    |


### Examples

```yaml
ExampleMob:
  Type: Skeleton
  AIGoalSelectors:
    - clear
    - rangedAttack{speed=1;smax=60;amin=20;radius=15}
```
Goal: bowAttack
--------------
*Aliases*: skeletonbowattack, bowshoot, bowmaster

An advanced ranged attack that can often cause the shooter to strafe backwards or clockwise.

### Attributes

| Attribute      | Aliases  | Description                                | Default |
|----------------|----------|--------------------------------------------|:-------:|
| speed          | s        | The attack speed modifier of this ai goal. |    1    |
| attackspeedmax | smax     |                                            |   60    |
| attackradius   | radius,r |                                            |   15    |


### Examples

```yaml
ExampleMob:
  Type: Skeleton
  AIGoalSelectors:
    - clear
    - bowattack{speed=1;smax=20;radius=15}
```
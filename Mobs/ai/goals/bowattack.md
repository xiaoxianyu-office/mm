## Description
An advanced ranged attack that can often cause the shooter to strafe backwards or clockwise.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed     | s         | Movement speed modifier                                              | 1       |
| attackradius | radius,r | The radius of the attack                                           | 15      |
| attackspeedmax | smax | The maximum attack speed                                             | 20      |


## Examples
```yaml
ExampleMob:
  Type: Skeleton
  AIGoalSelectors:
    - clear
    - bowattack{speed=1;radius=15}
```


## Aliases
- [x] skeletonbowattack
- [x] bowshoot
- [x] bowmaster
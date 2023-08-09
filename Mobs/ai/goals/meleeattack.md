## Description
Causes the mob to move to and melee attack its target


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| attackReach |         | The reach of the attack                                              |    4    |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - meleeattack{attackReach=6}
```
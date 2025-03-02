## Description
Causes the mob to move to and melee attack its target


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speedmodifier | speed, s | The speed modifier for the mob while this action is being taken   | 1       |
| followUnseen | fu     | Should the target be followed even if it is hidden from view         | false   |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - meleeattack{s=1;fu=false}
```
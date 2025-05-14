## Description
Checks whether the target player has the specified item group on cooldown.  
Do also check out the related [SetItemGroupCooldown mechanic](/Skills/Mechanics/SetItemGroupCooldown)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| group     | g         | the group to check against                                           |         |


## Examples
```yaml
  Conditions:
  - ItemGroupOnCooldown{g=teleportingitems}
```
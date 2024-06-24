## Description
Checks if the player is looking at either a block or an entity.  
Only usable by a player.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t, block, b, entity, e | The object to check against                             |         |


## Examples
```yaml
  Conditions:
  - lookingat{b=DIRT} true
```
```yaml
  TargetConditions:
  - isPlayer orElseCast fallbackmechanic
  - lookingat{e=COW} true
```
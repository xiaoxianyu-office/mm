## Description
Checks if the player is looking at either a block or an entity.  
Only usable by a player.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t, block, b, entity, e | The object to check against                             |         |
| distance  | d         | The distance of the generated raytrace. If the mob lookup behaves strangely, you can try to change this value | 5 |

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
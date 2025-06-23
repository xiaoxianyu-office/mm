## Description
Adds absorption hearts. Having maxShield as a greater value than amount
is recommended.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of the shield to give                                     | 1       |
| maxabsorb | maxshield, ma, ms | The maximum value the shield on the entity should be         | 1       |

  
## Examples
Gives absorption hearts to caster.
```yaml
  Skills:
  - shield{amount=50;maxShield=100} @self ~onSpawn
  - ...
```
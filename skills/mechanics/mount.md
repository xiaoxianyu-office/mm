## Description
Causes the casting mob to summon a specified MythicMob and mount it.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The type of MythicMob to summon                                      |         |

### Type Attribute
The MythicMob defines in type must be a valid MythicMob type (and is
case-sensitive). If an invalid type is specified the skill may throw an
error.


## Examples
This example would summon a Mythic Mob of the type "UndeadMount" and
make the caster mount it.
```yaml
CallSkeletalHorse:
  Skills:
  - mount{type=UndeadMount}
```
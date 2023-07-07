## Description
Summons a mob to mount the target. Will knock the current rider off if there is one.

## Attributes
| Attribute | Aliases | Description          | Default |
|-----------|---------|----------------------|---------|
| type    | t       | Passenger Mob Type | UNDEFINED     |

  

## Examples
```yaml
      Skills:
      summonPassenger{type=MyZombie} @trigger
```
Will summon the mob "MyZombie" to ride the trigger.
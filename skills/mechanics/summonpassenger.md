## Description
Summons a mob to mount the caster. Will knock the current rider off if there is one.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| passenger | p, rider, r, type, t | The type of the mob to set as the passenger               |         |
| stack | s | Sets whether to mount the summoned entity to the current passenger of the caster | false   |


## Examples
```yaml
  Skills:
  - summonPassenger{type=MyZombie}
```
Will summon the mob "MyZombie" to ride the caster of the mechanic.


## Aliases
- [x] passenger
- [x] summonRider
- [x] rider


<!--TAGS-->
<!--tag:Mount-->
<!--tag:Summon-->


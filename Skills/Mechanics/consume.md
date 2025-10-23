## Description
Damages each entity targeted for the given amount, and heals the casting
mob for each entity that takes damage this way.

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| damage    | d,dmg     | The amount of damage to deal                                         | 1       |
| heal      | h         | The amount of healing per mob damaged                                | 1       |
> This mechanic inherits every *inheritable* attribute of the [Damage](/Skills/Mechanics/Damage) mechanic


## Examples
Would consume all nearby zombies, healing the boss for 20 hp for each
zombie killed.
```yaml
  Skills:
  - consume{d=1000;h=20} @MobsInRadius{type=ZOMBIE;r=20}
```


<!--TAGS-->
<!--tag:Damage-->
<!--tag:Health-->
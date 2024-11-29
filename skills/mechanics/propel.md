## Description
Propels the caster of the mechanic towards the target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| velocity  | magnitude, v | The velocity at which the mob will be propelled                   | 1       |


## Examples
Propels the caster towards the damager if they are over 6 blocks away.
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - propel{v=1;delay=1} @trigger ~onDamaged ?~distance{d=>6}
```


<!--TAGS-->
<!--tag:Movement-->


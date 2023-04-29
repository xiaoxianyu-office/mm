## Mechanic: Propel
Propels the caster of the mechanic towards the target.


## Attributes

| Attribute      | Aliases         | Description                                        | Default Value |
|----------------|-----------------|----------------------------------------------------|---------------|
| velocity       | magnitude, v    | The velocity at which the mob will be propelled.   | 1             |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - propel{v=1;delay=1} @trigger ~onDamaged ?~distance{d=>6}
```
## Description
Sets the immunity ticks on the target. This should be delayed if used immediately during an attack since the ticks are applied after an event completes.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| ticks     | d, duration, t | The NoDamageTicks to set (for how many ticks the mobs will be invulnerable under normal circumstances) | 0 |


## Examples
Gives the caster invincibility after it attacks.
```yaml
  Skills:
  - setNoDamageTicks{ticks=0;delay=1} @self ~onAttack
```


## Aliases
- [x] setimmunityticks
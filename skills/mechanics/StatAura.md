## Description
Applies an [aura] to the target that applies a specific [stat] to them.  
The buff received is multiplied by the amount of stacks the aura has


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stat      | s         | The [stat] to apply                                           |<!--type:Stat-->|
| type      | t, modifier, mod, m | The [stat modifier] to use         | ADDITIVE<!--type:StatModifier-->|
| value     | val, v    | The value to use for the stat                                        | 0.0     |

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
The following aura will double the critical strike chance of the caster for 5 seconds
```yaml
  Skills:
  - stataura{auraName=exampleaura;d=100;stat=CRITICAL_STRIKE_CHANCE;type=COMPOUND_MULTIPLIER;val=2} @self
```


## Aliases
- [x] statbuff
- [x] statdebuff


<!-- LINKS -->
[aura]: /skills/mechanics/aura
[stat]: Stats
[stat modifier]: Stats#modifiers


<!--TAGS-->
<!--tag:Stat-->
<!--tag:Meta-Mechanic:Aura-->

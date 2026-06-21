## Description
Applies an [aura] component to the target that applies a specific [stat] to them.  
The buff received is multiplied by the amount of stacks the aura has


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stat      | s         | The [stat] to apply                                           |<!--type:Stat-->|
| type      | t, modifier, mod, m | The [stat modifier] to use         | ADDITIVE<!--type:StatModifier-->|
| value     | val, v    | The value to use for the stat                                        | 0.0     |


## Examples
The following aura will double the critical strike chance of the caster for 5 seconds
```yaml
  Skills:
  - aura{auraName=exampleaura;d=100;components=[
    - stat{stat=CRITICAL_STRIKE_CHANCE;type=COMPOUND_MULTIPLIER;val=2}
    ]} @self
```


## Aliases
- [x] stataura
- [x] stats


<!-- LINKS -->
[aura]: /skills/mechanics/aura
[stat]: Stats
[stat modifier]: Stats#modifiers

<!--TAGS-->
<!--tag:Stat-->

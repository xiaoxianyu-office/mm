## Description
Applies an aura to the target that triggers a skill when they damage
something. Can use any aura attribute

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |
| `<skill.var.damage-cause>`     |


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onattackskill | onattack, oa, onmelee, onhitskill, onhit, oh | [metaskill] to execute if the target hits something   |<!--type:Metaskill-->|
| cancelEvent | cE, canceldamage, cd | Whether or not to cancel the event that triggered the aura  | false   |
| damageAdd | add, a    | An optional static increase to the original hit's damage             | 0       |
| damageMultiplier | multiplier, m | An optional multiplier to the original hit's damage       | 1       |
| modDamageType | damagetype | The [type](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html) of the damage inflicted                                |<!--type:DamageCause--> |

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
```yaml
  Skills:
  - onAttack{oH=SuperPunch;cE=true;auraname=MyAura}
```


## Aliases
- [x] onhit


<!-- LINKS -->
[metaskill]: /Skills/Metaskills
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->

## Description
Applies an aura component to the target that triggers a skill when they damage
something. It is also possible to change the damage event itself.

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


<!-- LINKS -->
[metaskill]: /Skills/Metaskills
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders

## Aliases
- [x] onhit

<!--TAGS-->
<!--tag:Event-->
<!--tag:Damage-->

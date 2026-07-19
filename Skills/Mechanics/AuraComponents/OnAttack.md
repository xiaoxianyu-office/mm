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

> [!note]
> The aura only consumes a charge and applies `cancelEvent`, `damageAdd` or `damageMultiplier` **if the `onAttackSkill` executed successfully**: its chance roll succeeds, it is not on cooldown and all of its conditions pass. If the skill fails, the damage event is left untouched and no charge is consumed. If no `onAttackSkill` is configured, the execution always counts as successful.
>
> Additionally, `cancelEvent` takes precedence over the damage-modifying attributes: if `cancelEvent` is `true`, the hit is cancelled and `damageAdd` and `damageMultiplier` are ignored.


<!-- LINKS -->
[metaskill]: /Skills/Metaskills
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders

## Aliases
- [x] onhit

<!--TAGS-->
<!--tag:Event-->
<!--tag:Damage-->

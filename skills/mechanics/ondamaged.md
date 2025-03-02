## Description
Applies an aura to the target that triggers a skill when they take
damage. Can use any aura attribute

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |
| `<skill.var.damage-cause>`     |


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onHit     | ondamagedskill, ondamaged, od, onhitskill, oh | [Metaskill] to execute if the target is damaged     |<!--type:Metaskill-->|
| cancelEvent | cE, canceldamage | Whether or not to cancel the event that triggered the aura  | false   |
| damageSub | sub, s    | An optional static decrease (or increase if negative) to the original hit's damage | 0  |
| damageMultiplier | multiplier, m | An optional multiplier on the original hit's damage        | 1      |
| damagemodifiers | damagemods, damagemod | Allows the aura to apply damage modifiers. Also accepts a list, as shown in the example. Placeholders can be used as the modifier's amount (**Premium only**). |   |
| deflectProjectiles | deflect, reflect | Whether projectiles should be deflected               | false  |
| deflectconditions | dconditions | If `deflectProjectiles` is enabled, it will have to follow the specified set of conditions to work |<!--type:Conditions-->|
| modDamageType | damagetype | The [type](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html) of the damage that must be received in order to trigger the onHit metaskill |<!--type:DamageCause--> |

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
```yaml
  Skills:
  - onDamaged{
      auraName=damageResist;d=200;
      onTick=[
        - particles{p=flame;amount=10;hS=0.4}
      ];
      damageMods="FIRE 0.5, MAGIC 0.3, CUSTOM <caster.var.customresistance>"} @self ~onInteract
```


<!-- LINKS -->
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->

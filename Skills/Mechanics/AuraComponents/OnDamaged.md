## Description
Applies an aura component to the target that triggers a skill when they take
damage.

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

> [!note]
> The aura only consumes a charge and applies `cancelEvent`, `damageSub`, `damageMultiplier` or `damageModifiers` **if the `onHit` skill executed successfully**: its chance roll succeeds, it is not on cooldown and all of its conditions pass. If the skill fails, the damage event is left untouched and no charge is consumed. If no `onHit` skill is configured, the execution always counts as successful.
>
> Additionally, `cancelEvent` takes precedence over the damage-modifying attributes: if `cancelEvent` is `true`, the hit is cancelled and `damageSub`, `damageMultiplier` and `damageModifiers` are ignored.


## Examples
```yaml
  Skills:
  - aura{auraName=damageResist;d=200;components=[
    - onDamaged{
      onTick=[
        - particles{p=flame;amount=10;hS=0.4}
      ];
      damageMods="FIRE 0.5, MAGIC 0.3, CUSTOM <caster.var.customresistance>"} @self ~onInteract
    ]}
```


## Aliases
- [x] onDamage

<!-- LINKS -->
[aura]: /skills/mechanics/aura
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders

<!--TAGS-->
<!--tag:Event-->
<!--tag:Damage-->

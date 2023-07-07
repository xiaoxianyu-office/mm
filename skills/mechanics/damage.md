## Description

Damages the targeted entity.

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of damage to deal                                         | 1       |
| ignoreArmor | ia, i   | Whether or not to ignore armor, but will still use enchantment modifiers when calculating total damage                                                                       | false   |
| preventknockback | pkb, pk | Whether or not to prevent knockback                             | false   |
| preventimmunity  | pi      | Whether or not to ignore immunities                             | false   |
| element   | e, damagetype, type | Sets the type of damage to be inflicted                    |         |
| damagecause | dc, cause | Sets the damage cause for this damage mechanic.<br/> (This option is only available for 1.17+)                                                                     | entity_attack |
| ignoreenchantments |ignoreenchants, ie  | Whether or not to ignore enchantments when calculating total damage.<br>(This option is only available for 1.19+) | false         |
| noanger   | na        | Whether or not to generate anger when damaging the entity            | false   |
| ignoreinvulnerability | ignoreinvulnerable, ii | Whether or not to ignore invulnerability    | false   |
| ignoreshield | is     | Whether or not to ignore the shield blocking on the target           | false   |
| damageshelmet| dh     | Whether or not the helmet should be damaged                          | false   |
| ignoreeffects| ieff   | Whether or not effects should be ignored                             | false   |
| ignoreresistance | ir | Whether or not resistance should be ignored                          | false   |

### DamageCause
This attribute is only available in newer MM 5.0 builds.
All available damage causes can be found on [spigot javadocs](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html)

Note: Only `entity_attack`, `entity_sweep_attack`, `thorns`, `sonic_boom`, `entity_explosion`, and `projectile` will return an entity damager, 
meaning that `<trigger.name>` will not return "Unknown".

### Elements
As seen above, the damage mechanic offers the ability to set an "element" for the damage, like so:

```yaml
- damage{amount=10;element=FIRE} @target ~onUse
- damage{amount=10;element=ICE} @target ~onUse
```

This element can buy named anything, and can be used in a mob's DamageModifiers to alter resistance to the damage type as needed:
```yaml
DamageModTest: 
  Type: COW 
  DamageModifiers:
  - LIGHTNING 0.1
  - FIRE 2.0
  - AIR 1.0
  - ICE 0.5 
  Skills:
  - message{m="Damaged by <skill.var.damage-type> for <skill.var.damage-amount>"} @PIR{r=50} ~onDamaged
```
These options can also be used in the "onDamaged" aura, using the `damageMods="FIRE 0.5"` attribute.

## Examples
```yaml
  Skills:
  - damage{amount=20;ignoreArmor=true} @target ~onTimer:20
```

This skill above does 20 damage (10 hearts), ignoring armor, to the
mob's target every 1 second (20 ticks).
```yaml
FreezeBlast:
  Skills:
  - effect:sound{s=block.fire.extinguish;v=1;p=0.5} @PIR{r=6}
  - effect:particles{p=explode;a=8;vs=0.5;hs=0.5;s=0;y=1;repeat=5;repeatInterval=20} @PIR{r=6}
  - effect:particles{p=drip_water;a=10;vs=0.5;hs=0.5;s=0;y=1;repeat=5;repeatInterval=20} @PIR{r=6}
  - potion{t=SLOW;d=120;l=6} @PIR{r=6}
  - damage{a=120;pkb=true} @PIR{r=6}
```
A more complex use of the **damage** mechanic can give illusions of say
Ice attacks like the example above. Which uses effects to make the
targets of the mob appear as if they were frozen by using particles (On
a repeating interval to create a sort of lingering frost effect as well)
and inflicting Slowness level 7 (which is -105% movement speed.) slowing
the mob to a halt. Additionally, the mechanic inflicts 120 damage (60
hearts) to players within 6 blocks.

##

**Premium Example**
```yaml
  Skills:
  - damage{amount=<caster.var.somevariable> * 0.5 + 1} @target ~onTimer:20
```
This skill above does "<caster.var.somevariable> * 0.5 + 1" damage
if the varibute: <caster.var.somevariable>'s value is 5,this mechaine will does 3.5 damage


## Aliases
- [x] d
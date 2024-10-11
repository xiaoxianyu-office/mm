## Description

Shoots an arrow or item-projectile at the targeted entity or location
that deals damage. The shoot-mechanic has been significantly changed in
version 2.4. See below for both how it worked prior and after those
additions.

Added most of the options from the Projectile mechanic to Shoot & Volley in MM 4.11


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | Type of projectile to shoot. Can be "arrow", "snowball", "egg", "enderpearl", or "potion" added "trident", "splash_potion", and "lingering_potion" in MM 4.11 | arrow   |
| damage               | d, amount  | How much damage the projectile will cause                                                 | 5       |
| velocity             | v          | The velocity of the projectile                                                            | 1       |
| maxDistance          | md         | The maximum distance the projectile will travel                                           | 64      |
| vspread              | vs         | The vertical hit radius of the projectile                                                 | 0       |
| hspread              | hs         | The horizontal hit radius of the projectile                                               | 0       |
| poweraffectsvelocity | pav        | Whether the mobs power level should affect the velocity of the projectile                 | true    |
| interval             | int, i     | How often per second the projectile creates a tick-event                                  | 4       |
| ontickskill          | ontick, ot | The meta-skill to execute on each tick/interval of the projectile                         | None |
| onhitskill           | onhit, oh  | The meta-skill to execute when the projectile hits its target                             | None |
| onendskill           | onend, oe  | The meta-skill to execute when the projectile misses and ends                             | None |
| bounce               |            | Whether the projectile will bounce when it hits something                            | false |
| pickup               |            | Can pickup the item.                                                        | false |
| expiration           | duration, expire, e | How many ticks should the projectile exist for after it has landed before it gets removed                                                                  | 100     |
| accuracy             | ac, a      | Accuracy of the projectile                                          | 1 |
| knockback            | kb         | knockback strength of the projectile                                               | 0 |
| piercelevel          | pl         | The amount of times the arrow can pierce through an entity                   | 0 | 
| ignoreArmor          |            | Whether or not to ignore armor, but will still use enchantment modifiers when calculating total damage                                                                                 |     | 
| preventImmunity      |            | Whether or not to ignore immunities                                        |     | 
| preventKnockback     |            | Whether or not to prevent knockback                                         |     |
| ignoreenchants       |            | Whether or not to ignore enchantments when calculating total damage. This option is only available for 1.19+)                                                                     |     |
| damageType           |            | Sets the type of damage to be inflicted ([Extra info](/skills/mechanics/damage#elements))                                      |     | 
| damageCause          |            | Sets the damage cause for this damage mechanic ([Extra info](/skills/mechanics/damage#damagecause))                                                                        |     | 
| verticaloffset       | vo         | The vertical offset of the shot projectile               | 0       |
| horizontaloffset     | ho         | The horizontal offset of the shot projectile             | 0       |
| gravity   | g         | Whether the projectile should be affected by gravity                 | true    |
| startyoffset | syo    | The starting y offset of the projectile                              | 0       |
| adjustvelocity | av   | If the caster is a player, adjusts the velocity and direction as if the player was shooting it themselves | true  |
| calculatefiringangle | cfa        | If this is set and the projectile has `gravity`, the projectile will  trace an arc in the air before landing at the target location                                  | false   | 
| verticalnoise  | vn  | The vertical noise (randomness) of the shot projectile | ((1-`accuracy`)*45)/10 |
| horizontalnoise | hs  | The horizontal noise (randomness) of the shot projectile   | (1-`accuracy`)*45 |         
| potiontype     | ptype, effect, pt, pe | The type of the potion applied to the projectile, if POTION | SLOW |
| potionduration | pduration, pd | The duration of the potion effect                           | 100     |


## Examples
```yaml
ArrowBarrage:
  Skills:
  - shoot{type=ARROW;velocity=5;damage=10}
  - delay 10
  - shoot{type=ARROW;velocity=5;damage=10}
  - delay 10
  - shoot{type=ARROW;velocity=5;damage=10}
  - delay 10
  - shoot{type=ARROW;velocity=5;damage=10}
  - delay 10
  - shoot{type=ARROW;velocity=5;damage=10}
```


## Aliases
- [x] shootprojetile
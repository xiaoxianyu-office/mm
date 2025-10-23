## Description

Shoots an arrow or item-projectile at the targeted entity or location
that deals damage. The shoot-mechanic has been significantly changed in
version 2.4. See below for both how it worked prior and after those
additions.

Added most of the options from the Projectile mechanic to Shoot & Volley in MM 4.11


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | Type of projectile to shoot.                                         | arrow<!--type:Shoot_Type-->|
| damage    | d, amount | How much damage the projectile will cause                            | 5       |
| velocity  | v         | The velocity of the projectile                                       | 1       |
| maxDistance | md      | The maximum distance the projectile will travel                      | 64      |
| poweraffectsvelocity | pav | Whether the mobs power level should affect the velocity of the projectile                 | true    |
| interval  | int, i    | How often per second the projectile creates a tick-event             | 4       |
| item      |           | The item being shot. Only applicable to some projectile types        |<!--type:Material-->|
| ontickskill | ontick, ot, m, meta, s, skill | The meta-skill to execute on each tick/interval of the projectile |<!--type:Metaskill-->|
| onhitskill | onhit, oh| The meta-skill to execute when the projectile hits its target        |<!--type:Metaskill-->|
| onendskill | onend, oe| The meta-skill to execute when the projectile misses and ends        |<!--type:Metaskill-->|
| bounce    |           | Whether the projectile will bounce when it hits something            | false   |
| pickup    |           | Can pickup the item.                                                 | false   |
| expiration | duration, expire, e | How many ticks should the projectile exist for after it has landed before it gets removed                                                                         | 100     |
| accuracy  | ac, a     | Accuracy of the projectile                                           | 1       |
| knockback | kb        | knockback strength of the projectile                                 | 0       |
| piercelevel | pl      | The amount of times the arrow can pierce through an entity           | 0       | 
| verticaloffset       | vo         | The vertical offset of the shot projectile               | 0       |
| horizontaloffset     | ho         | The horizontal offset of the shot projectile             | 0       |
| forwardoffset | startfoffset, sfo | The forward offset of the shot projectile | 1 |
| sideoffset | soffset, so | The side offset of the shot projectile | 0 |
| startsideoffset | ssoffset, sso | The side offset of the shot projectile. Yes, it is the same as the above, but *this* attribute has placeholder support. | `sideOffset's value`|
| gravity   | g         | Whether the projectile should be affected by gravity                 | true    |
| startyoffset | syo    | The starting y offset of the projectile                              | 0       |
| adjustvelocity | av   | If the caster is a player, adjusts the velocity and direction as if the player was shooting it themselves | true  |
| calculatefiringangle | cfa        | If this is set and the projectile has `gravity`, the projectile will  trace an arc in the air before landing at the target location                                  | false   | 
| verticalnoise  | vn  | The vertical noise (randomness) of the shot projectile | ((1-`accuracy`)*45)/10 |
| horizontalnoise | hn  | The horizontal noise (randomness) of the shot projectile   | (1-`accuracy`)*45 |         
| fromorigin| fo        | Whether the projectile should be shot from the origin of the mechanic| false   |  
> This mechanic inherits every *inheritable* attribute of the [Damage](/Skills/Mechanics/Damage) mechanic

### Type Attribute
The types for the projectile can be
| Type            | Aliases        |
|-----------------|----------------|
| `ARROW`         |                |
| `SNOWBALL`      |                |
| `EGG`           |                |
| `ENDERPEARL`    |                |
| `POTION`        | `SPLASH_POTION`|
| `LINGERING_POTION` |             |
| `ITEM`          |                |
| `BLOCK`         | `FALLING_BLOCK`|
| `TRIDENT`       |                |

#### Potion Type Attributes
These attributes apply if the projectile is of `type` `POTION`
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| potiontype     | ptype, effect, pt, pe | The type of the potion applied to the projectile, if POTION | SLOW<!--type:PotionEffectType-->|
| potionduration | pduration, pd | The duration of the potion effect                           | 100     |
| potionlevel    | plevel, lvl, pl | The level of the potion effect                            | 1       |
| force          | overwrite, ow, override, or | Whether to override the effect on the target if already applied    | false  |
| potioncolor | pc      | The color of the potion                                              | #FFFFFF<!--type:Color--> |
| hasParticles | particles | Whether not to show the status effect particles.                  | true    |
| hasIcon   | icon  | Whether not to show the status effect icon.                              | true    |
| ambientparticles | ambient  | Whether to show ambient particles.                             | false   |


#### Trident Type Attributes
These attributes apply if the projectile is of `type` `TRIDENT`
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| tridentitem | titem, ti | The trident item                                                   |         |

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


<!--TAGS-->
<!--tag:Projectile-->
<!--tag:Meta-Mechanic-->
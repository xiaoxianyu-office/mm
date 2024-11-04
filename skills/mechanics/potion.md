## Description
Applies a potion effect to the target entity, which is usually
frequently used on custom mob creations and a quite powerful tool; as it
allows for countless interesting applications. See the [spigot javadocs](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html) for a complete list of available potion
effects.

Potion effects are currently the only way to make mobs invisible, with
the exception of the armorstand mobtype which has it's own attribute for
indefinite invisibility. Extremely high modifier-levels may have obscure
effects.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t, effect | The type of [potion effect](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html) to apply.   | SLOW<!--type:PotionEffectType--> |
| duration  | d         | The duration of the effect in ticks [1].                             | 100     |
| level     | lvl, l    | The modifier-level of the potion effect. The real level is level's value +1.| 0|
| force     | overwrite, ow, override, or | Whether not to override the current potion effect or not. | false |
| hasParticles | particles, p | Whether not to show the status effect particles.               | true    |
| hasIcon   | icon,  i  | Whether not to show the status effect icon.                          | true    |
| ambientparticles | ambient, a | Whether to show ambient particles.                           | false   |


## Examples
This example skill-configuration will strongly slow down the target for
10 seconds (200 ticks) and deal 5 hearts of damage to it.
```yaml
Cripple:
  Skills:
  - potion{type=SLOW;duration=200;level=4}
  - damage{amount=10}
```
> 20 ticks = 1 second
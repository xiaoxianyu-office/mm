## Description
Throws a potion at the targeted entity or location, causing the splash
potion effect of the given type to all entities hit.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The type of [potion effect](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/potion/PotionEffectType.html) to apply    |         |
| duratio   | d         | The duration of the effect, in ticks                                 | 100     |
| level     | l         | The level of the potion effect                                       | 1       |
| velocity  | v         | The velocity of the thrown potion                                    | 1       |
| hasParticles | particles or p | Whether not to show the status effect particles              | true    |
| hasIcon   | icon or i      | Whether not to show the status effect icon                      | true    |


## Examples
Throws a potion at the target that slows them down.
```yaml
ThrownCripplingPotion:
  Skills:
  - shootpotion{type=SLOW;duration=200;level=4;velocity=5} @target
```
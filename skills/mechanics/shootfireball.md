## Description
Shoots a fireball from the mob towards the target entity or location.

> Caution!  
> The large version of this fireball can grief blocks.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| yield     | strength, y, s | The yield (power) of the fireball's explosion                   | 1       |
| velocity  | v         | The velocity of the fireball                                         | 1       |
| fireTicks | ft        | How long (in ticks) fire left behind by the fireball will persist    | 0       |
| incendiary| i         | (true/false) Whether the fireball will leave behind fire             | false   |
| charged   | c         | Whether the fireball is charged                                      | false   |
| fromorigin| fo        | Whether the fireball should be shot from the [origin]                | false   |
| playsound | ps        | Whether or not to play the fireball launching sound when it is created | false |
| smallfireball | small,sml | Whether or not to use the smaller blaze fireball instead of the ghast fireball                                                                                       | false   |
| type      | t         | The type of the fireball                                             | SMALL<!--type:ShootFireball_Type--> |
| item      | material  | The [material] of the fireball, if ITEM type was used           | BLAZE_POWDER<!--type:Material-->|


### Type Attribute
| Available Types |
|-----------------|
| NORMAL
| SMALL
| LARGE
| WITHER
| DRAGON
| ITEM


## Examples
This example would shoot a barrage of 3 fast-moving fireballs at the
target.
```yaml
FireballBarrage:
  Skills:
  - shootfireball{y=1;v=4} @target
  - delay 10
  - shootfireball{y=1;v=4} @target
  - delay 10
  - shootfireball{y=1;v=4} @target
```


## Aliases
- [x] fireball


<!-- LINKS -->
[origin]: /Skills/Targeters/Origin
[material]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html


<!--TAGS-->
<!--tag:Projectile-->

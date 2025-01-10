## Description
Plays a sound from either the vanilla game or a resource pack at the targeted entity or location. An extensive list of sounds can be found [here](https://misode.github.io/sounds/). Using multiple sounds stacked together can give the impression of an entirely new sound.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| sound     | s         | The sound to play                             | entity.zombie.attack_iron_door<!--type:Sound-->|
| pitch     | p         | The pitch of the sound. Can be between 0.01 and 2.0                  | 1.0     |
| volume    | v         | The volume of the sound.                                             | 1.0     |
| radius    | r         | The radius in which the sound will be heard                      | `volume`*16 |
| soundcategory | category, sc | The category at which the sound is played, useful for resourcepacks | MASTER<!--type:SoundCategory-->|
| audience  |           | The [audience] of the effect                                         | world<!--type:Audience--> |

### SoundCategory Attribute
A list of sound categories can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/SoundCategory.html).

### Volume Attribute
The “volume” attribute, while above the value of "1", doesn't define the percentage of the loudness of the sound, but rather determines how far (measured in blocks) the sound can be heard at maximum volume.

The formula for this is v * 16 = maxvolume distance. For example if you use “1” for the volume attribute, the sound can be heard at maximum volume in a radius of 16 blocks around the source. If you used “20” however, the sound can be heard at maximum volume in a 320 block radius! (20 * 16)

While the value is between 0 and 1, the sound is still played in a 16 blocks radius, but with diminished volume, with 0.1 being 10% of normal volume, 0.4 being 40% of normal volume and so on


## Examples
```yaml
EndermanAttack:
  Skills:
  - sound{s=entity.enderman.scream} @self
```
##
The below example plays a sound from your resource pack. A good guide on adding custom sounds can be found [here](https://mcmodels.net/guides/4-sounds).
```yaml
BossSoundEffect:
  Skills:
  - sound{s=yoursound:example.sound.name_1} @self
```


## Aliases
- [x] effect:sound
- [x] s
- [x] e:sound
- [x] e:s


<!-- LINKS -->
[audience]: /Skills/Audience


<!--TAGS-->
<!--tag:Effect:Sound-->
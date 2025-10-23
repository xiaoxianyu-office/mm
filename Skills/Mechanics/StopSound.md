## Description
Stops a sound from playing from either the vanilla game or a resource pack for the targeted entity. A good list of sounds can be found [here](https://minecraft.wiki/w/Sounds.json#sound_events). Use the “sound event” column.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| sound     | s         | Sound to stop playing                         | entity.zombie.attack_iron_door<!--type:Sound--> |
| soundcategory | source, sc, category | The category at which the sound is played, useful for resourcepacks | MASTER<!--type:SoundCategory-->|

### SoundCategory Attribute
A list of sound categories can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/SoundCategory.html).


## Examples
```yaml
SilenceEndermanSkill:
  Skills:
  - stopsound{s=entity.enderman.scream} @PIR{r=10}
```


## Aliases
- [x] effect:stopsound
- [x] e:ss
- [x] ss


<!--TAGS-->
<!--tag:Effect:Sound-->

## Description
Plays the target block's hit (damage) sound.  

> **This is a [Paper-Only] mechanic!**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| pitch     | p         | The pitch of the sound. Can be between 0.01 and 2.0                  | 1.0     |
| volume    | v         | The volume of the sound.                                             | 1.0     |

### Volume Attribute
The “volume” attribute doesn't define the percentage of the loudness of the sound, but rather determines how far (measured in blocks) the sound can be heard at maximum volume.  

The formula for this is `v * 16 = max volume distance`. For example if you use “1” for the volume attribute, the sound can be heard at maximum volume in a radius of 16 blocks around the source. If you used “20” however, the sound can be heard at maximum volume in a 320 block radius! (20 * 16)


## Example
```yaml
  Skills:
  - blockhitsound @targetlocation
```


## Aliases
- [x] blockhitsound


<!-- LINKS -->
[Paper-Only]: https://papermc.io/downloads/all


<!--TAGS-->
<!--tag:Effect:Sound-->
<!--tag:Paper-Only-->

## Description
Creates a wave of the specified blocks, with varying shapes, speeds and blocks.

Note that the blockwave effect will never actually change any blocks in the world and thus will never grief the environment in any way. The changes made this effect are purely cosmetic, no actual blocks are changed and everything will always return to its original state.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m         | The [material] used for the blockwave                                | <!--type:Material-->|
| radius    | r         | The radius of the blockwave effect                                   | 2       |
| radiusy   | ry        | The y radius of the blockwave effect                                 |`radius` |
| duration  | d         | Duration of the effect in ticks                                      | 15      |
| shape     | s         | The shape of the effect (Sphere/Cube)                                | sphere<!--type:Shape-->|
| velocity  | v         | The speed of the effect                                              | 0.2     |
| horizontalvelocity | velocityh, vh | The speed of the effect in the horizontal direction     | 0       |
| specificvelocities | sv | Whether to make use of the `vx`, `vy` and `vz` attributes          | false   |
| velocityx | vx        | The speed of the effect on the x axis                                | 0       |
| velocityy | vy        | The speed of the effect on the y axis                                | 0       |
| velocityz | vz        | The speed of the effect on the z axis                                | 0       |
| noise     | n         | The noise of the effect                                              | 0       |
| hidesourceblock | hidesource, hsb, hs  | Whether to hide the source block                    | true    |  
| ignoreair | ia        | Whether air blocks should be ignored                                 | true    |

### Material Attribute
If material is left blank, it will use whatever material type it is used on. 
Example: if you leave it blank and use it on a villager building, you will see the blocks of the building used in the blockwave. 


## Examples
```yaml
  Skills:
  - blockwave{duration=100;material=stone;radius=5;radiusY=5;velocity=10;shape=sphere} @selflocation
```
> Creates a stone blockwave in a sphere shape starting at your self location


## Aliases
- [x] effect:blockWave
- [x] e:blockWave


<!-- LINKS -->
[material]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html


<!--TAGS-->
<!--tag:Effect-->
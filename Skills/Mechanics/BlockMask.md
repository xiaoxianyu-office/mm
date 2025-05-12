## Description 
Creates a mask of blocks around the specified target. The blocks created or changed by this effect will disappear or rather reset to their former state after the specified duration expired. Resetting the blocks at an earlier point in time can be achieved by using the blockunmask-effect (see example below).

Note that the blockmask effect will never actually change any blocks in the world and thus will never grief the environment in any way. The changes made this effect are purely cosmetic, no actual blocks are changed and everything will always return to its original state.

The material attribute accepts as valid values the [Bukkit name](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) that is relative to it.

Bukkit material/block names can be acquired in-game. Simply hold the block you want to use for the effect in your hand and then use the command “/itemdb”. This command will output the bukkit-material info along with some other info, including the data value of the block. This command should work on any bukkit/spigot server.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | mat, m, block, b | The [type of block](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/Material.html) used for the blockmask                      | GRAVEL<!--type:Block--> |
| radius    | r         | The radius of the blockmask effect                                   | 0       |
| radiusy   | ry        | The y component of the radius                                        | `radius`|
| noise     | n         | Defines the randomness of the effect                                 | 0       |
| duration  | d         | Duration of the effect in ticks                                      | 0       |
| shape     | s         | The shape of the effect. `Sphere`/`Cube`                             | SPHERE<!--type:Shape-->|
| noair     | na        | Mask no air blocks only                                              | true    |
| onlyair   | oa        | Mask air blocks only                                                 | false   |
| audience  |           | The [audience] of the effect                                         | nearby<!--type:Audience--> |
| occ       | o, oc     | If onlyair is used, target transparent blocks as well                | true    |

### Duration Attribute
there are 20 ticks in 1 second, and setting duration to 0 will have an infinite duration. 

### Shape Attribute
`Sphere` and `Cube` are the only shapes available.


## Examples
Creates a netherrack environment around the casting mob. Leaving the duration on 0 ticks will cause the blocks to stay in their new fake form until manual block updates are provided or players relog into the game.

```yaml
- effect:blockmask{m=netherrack;r=5} @self ~onTimer:1200
```

##

Creates a layer of ice underneath the feet of all players within a 50 block radius, causing them to have a constantly slippery walk.

```yaml
- effect:blockmask{m=ice;r=2;d=20} @PIR{r=50} ~onTimer:5
```
##

```yaml
- effect:blockmask{m=ice;r=2;d=20;onlyair=true} @origin ~onTimer:5 # this will replace air and transparent blocks (i.e. stairs, slabs and glass) with ice
- effect:blockmask{m=ice;r=2;d=20;onlyair=true;occ=false} @origin ~onTimer:5 # this will replace only air with ice
```
##

Will forcibly reverse all effects created by the blockmask effect in the specified radius. The blockunmask effect doesn't have any syntax options except for “radius”.

```yaml
- effect:blockunmask{r=30}
```


## Aliases
- [x] effect:blockMask
- [x] e:blockMask


<!-- LINKS -->
[audience]: /Skills/Audience


<!--TAGS-->
<!--tag:Effect-->
## Description 
Creates a particle effect at the targeted entity or location.

A list of particle types can be found **[here](/Skills/Mechanics/Particle/Particle-Types)**. 

[All of the spigot particle effects listed in the javadocs should be acceptable as well.](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)


## Attributes
### General Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| particle  | p         | The [particle type] to use.                                          | reddust<!--type:Particle-->|
| mob       | m, t      | The entity to spawn as the particle. Cannot be the original entity. **Premium Only**.                                                                                  |<!--type:Mob-->|
| amount    | count, a  | The number of particles to create                                    | 10      |
| spread    | offset    | The vertical spread of the particles                                 | 0       |
| hSpread   | hs        | The horizontal spread of the particles                               | `spread`|
| vSpread   | vs, yspread, ys| The spread of the particles on the y axis. Overwrites `spread`  | `spread`|
| xSpread   | xs        | The spread of the particles on the x axis. Overwrites `hSpread` on that axis       | hSpread |
| zSpread   | zs        | The spread of the particles on the z axis. Overwrites `hSpread` on that axis                            | hSpread |
| speed     | s         | The “speed” of the particles. If a particle has a [DataType](/Skills/Mechanics/Particle/Particle-Types#datatypes), this attribute will behave inconsistently. | 0    |
| yOffset   | y         | The Y offset of the particles from the target                        | 0       |
| viewDistance | vd     | The distance the particles are rendered                              | 128     |
| fromorigin| fo        | Should the particles be generated from the origin of the mechanic    | false   |
| directional| d        | Does the particle use directional travel. The [particle type] used must not have additional data (extra attributes)                                                             | false   | 
| directionReversed| dr | Reverses the direction of the particles.                             | false   | 
| direction | dir       | Specifies a vector for the particles to move towards.          | 0,0,0 (x,y,z) | 
| fixedyaw  | yaw       | Sets the yaw of the location target(s) of the mechanic. This is ignored if it remains -1111 | -1111   |
| fixedpitch| pitch     | Sets the pitch of the location target(s) of the mechanic. This is ignored if it remains -1111 | -1111   |
| audience  |           | The [audience] of the particle effect                                | nearby<!--type:Audience--> |
| color     | c         | The color of the particle, if supported                              |<!--type:Color-->|
| exactoffsets | eo     | Changes the formula with which random spawn locations for the particles are computed | false |


#### Extra Attributes
Depending on the specific [particle type] used, extra attributes will become available to use inside particle-related mechanics too. you can find more by accessing the specific particle's page from the [particle types wiki page]

#### Mob-Type Particles \[**Premium Only**\]
This particle type will replace the spawned particle with the selected entity. The entity will act as a normal one, being able to attack, be hit, activate skills and so on. The entity will have no parent/owner relationship with the caster.

### Entity-Only Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| useEyeLocation | uel  | (true/false) Whether to base the particles on the entity's eyes      | false   |
| forwardOffset | startfoffset, sfo | The forward-offset from the targeted entity, does not work when `directional` is set to true | 0       |
| sideOffset| soffset, sso | The side-offset from the targeted entity, does not work when `directional` is set to true | 0 |

## Examples
```yaml
  Skills:
  - effect:particles{particle=flame;amount=200;hS=1;vS=1;speed=5} @self
  - ...
```
```yaml
  Skills:
  - effect:particles{particle=block;m=dirt;amount=100;hS=1;vS=1} @self
  - ...
```
```yaml
  Skills:
  - particles{particle=flame;a=10;hs=0.3;vs=0.3;y=0.3;s=0.1125} @self
  - ...
```

## Aliases
- [x] effect:particles
- [x] effect:particle
- [x] particles
- [x] particle
- [x] e:particles
- [x] e:particle
- [x] e:p


<!-- LINKS -->
[particle type]: /Skills/Mechanics/Particle/Particle-Types
[particle types wiki page]: /Skills/Mechanics/Particle/Particle-Types


<!--TAGS-->
<!--tag:Effect:Particle-->
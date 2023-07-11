## Mechanic: Slash
The Slash meta-mechanic can execute other skills in a slash-shaped pattern. The exact shape, size, location, rotation and other such elements of the slash itself can be tweaked via the attributes below.

## Attributes
| Attribute      | Aliases     | Description                                             | Default Value |
|----------------|-------------|---------------------------------------------------------|:-------------:|
| onStartSkill   | onStart, oS | Meta-Skill executed at the start of the slash           |               |
| onEndSkill     | onEnd, oE   | Meta-Skill executed at the end of the slash             |               |
| onPointSkill   | onPoint, oP | Meta-Skill executed at every point of the slash         |               |
| onHitEntitySkill | onHitEntity, ohe, oh | Meta-Skill executed when a point of the slash hits an entity. only triggered once per entity for every execution of the slash mechanic                 |               |
| Points         | p           | The amount of points in the slash                       | 32            |
| Duration       | d           | The amount of ticks the slash should "travel" for. A value of 0 executes an instant slash                                                                         | 0             |
| Width          | w           | The width of the slash. Increasing this value makes the slash's arc less arched                                                                                   | 1            |
|  Height        | h           | The height of the slash. Increasing this value makes the slash's arc more arched                                                                                   | 1             |
| Angle          | arc, a      | The size of the arch in degrees                         | 180           |
| xOffset        | xo, x       | The offset on the X axis                                | 0             |
| yOffset        | yo, y       | The offset on the Y axis                                | 0             |
| zOffset        | zo, z       | The offset on the Z axis                                | 0             |
| ForwardOffset  | foffset, fo | Forward offset                                          | 0             |
| Pitch          |             | The pitch rotation                                      | 0             |
| Yaw            |             | The yaw rotation                                        | 0             |
| Roll           |             | The roll rotation                                       | 0             |
| Radius         | r           | The hit radius                                          | 1             |
| Rotation       | rot         | The rotation of the slash, in the x,y,z format. Same as using pitch/yaw/roll                                                                           | 0,0,0         |
| MatchCasterDirection | matchPlayerDirection, matchDirection, mcd, mpd, md, direction                    | Matches the direction of the slash to the caster's facing direction                    | true          |
| FromOrigin     |             | If the slash should start in the origin of the metaskill | false        |
| HitConditions  | conditions, cond, c, oC, hC | List of [Inline Conditions](/Skills/conditions/in-linetargetconditions) that an entity must met to be hit by the slash mechanic            |               |

## Examples
```yaml
ExampleSkill:
  Skills:
  - slash{y=1.8;w=4;h=2;mpd=true;a=180;oP=[ - effect:particles{p=CRIT} ];roll=<random.-45to45>}
```
```yaml
SlashSword:
  Id: NETHERITE_SWORD
  Skills:
  - slash{y=1.8;w=4;h=40;mpd=true;a=45;radius=2;
      oP=[ - effect:particles{p=SPARK} ];
      oH=[ - damage{a=2} ];
      roll=<random.-30to30>;fo=5;duration=5} @self ~onUse
```
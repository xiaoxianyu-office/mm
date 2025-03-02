## Description
The Slash meta-mechanic can execute other skills in a slash-shaped pattern. The exact shape, size, location, rotation and other such elements of the slash itself can be tweaked via the attributes below.

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onStartSkill   | onStart, oS | Meta-Skill executed at the start of the slash           |<!--type:Metaskill-->|
| onEndSkill     | onEnd, oE   | Meta-Skill executed at the end of the slash             |<!--type:Metaskill-->|
| onPointSkill   | onPoint, oP | Meta-Skill executed at every point of the slash         |<!--type:Metaskill-->|
| onHitEntitySkill | onHitEntity, ohe, oh | Meta-Skill executed when a point of the slash hits an entity. Only triggered once per entity for every execution of the slash mechanic                 |<!--type:Metaskill-->|
| Points         | p           | The amount of points in the slash                       | 32            |
| specificStep   | ss          | Define a specific step/index from the generated points which should be shown, when the supplied value is greaten than 0 | 0 |
| Duration       | d           | The amount of ticks the slash should "travel" for. A value of 0 executes an instantaneous slash                                                                         | 0             |
| Width          | w           | The width of the slash. Increasing this value makes the slash's arc less arched                                                                                   | 1            |
|  Height        | h           | The height of the slash. Increasing this value makes the slash's arc more arched                                                                                   | 1             |
| Angle          | arc, a      | The size of the arch in degrees                         | 180           |
| xOffset        | xo, x       | The offset on the X axis                                | 0             |
| yOffset        | yo, y       | The offset on the Y axis                                | 0             |
| zOffset        | zo, z       | The offset on the Z axis                                | 0             |
| ForwardOffset  | foffset, fo | Forward offset                                          | 0             |
| targetxoffset  | txo, tx     | Target X-axis offset                                    | 0             |
| targetyoffset  | tyo, ty     | Target Y-axis offset                                    | 0             |
| targetzoffset  | tzo, tz     | Target Z-axis offset                                    | 0             |
| Pitch          |             | The pitch rotation                                      | 0             |
| Yaw            |             | The yaw rotation                                        | 0             |
| Roll           |             | The roll rotation                                       | 0             |
| Radius         | r           | The hit radius                                          | 1             |
| Rotation       | rot         | The rotation of the slash, in the x,y,z format. Same as using pitch/yaw/roll                                                                           | 0,0,0         |
| MatchCasterDirection | matchPlayerDirection, matchDirection, mcd, mpd, md, direction                    | Matches the direction of the slash to the caster's facing direction                    | true          |
| directionTowardsTarget | dtt | If the yaw/pitch should be calculated to aim to the target | false      |
| FromOrigin     |             | If the slash should start in the origin of the metaskill | false        |
| HitConditions  | conditions, cond, c, oC, hC | List of [Inline Conditions](/Skills/Inline-Conditions) that an entity must met to be hit by the slash mechanic            |<!--type:Conditions-->|

## Examples
This is a basic example of how a slash mechanic might look like once implemented
```yaml
ExampleSkill:
  Skills:
  - slash{y=1.8;w=4;h=2;mpd=true;a=180;oP=[ - effect:particles{p=CRIT} ];roll=-45to45}
```
##
If you have [Crucible] installed, then the following is an example on how you can put the slash mechanic into an item
```yaml
SlashSword:
  Id: NETHERITE_SWORD
  Skills:
  - slash{y=1.8;w=4;h=4;mpd=true;a=45;radius=2;roll=-30to30;fo=5;duration=5;
      oP=[ - effect:particles{p=SPARK} ];
      oH=[ - damage{a=2} ]
      } @self ~onUse
```

[Crucible]: https://mythiccraft.io/index.php?resources/crucible-create-unbelievable-mythic-items.2


<!--TAGS-->
<!--tag:Meta-Mechanic-->
## Description
The Polygon meta-mechanic can execute other skills in a polygon-shaped pattern. The exact number of vertices, the scale, the duration and other such elements of the polygon itself can be tweaked via the attributes below.

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onPointSkill   | onPoint, oP | Meta-Skill executed at every vertex                     |<!--type:Metaskill-->|
| onStarSkill    | onStar, oS  | Meta-Skill executed at the "start of the "star" of the polygon, aka the figure formed inside of the polygon by tweaking the "skip" parameter                     |<!--type:Metaskill-->|
| onEdgeSkill    | onEdge, oE  | Meta-Skill executed on the segments that connects the vertices|<!--type:Metaskill-->|
| onHitEntitySkill | onHitEntity, ohe, oh | Meta-Skill executed when the polygon hits an entity. Only triggered once per entity inside the polygon area for every execution of the polygon mechanic |<!--type:Metaskill-->|
| Points         | p           | The amount of vertices of the polygon                   | 32            |
| Duration       | d           | The amount of ticks the polygon should take to fully form. A value of 0 creates a polygon instantly                                                              | 0             |
| DistanceBetween| distance, density, db | The distance between points in the polygon    | 0.1           |
| Scale          | size, s     | The scale of the polygon                                | 1             |
| Skip           | star, sv    | The number of points to skip for star-like shapes       | 2             |
| xOffset        | xo, x       | The offset on the X axis                                | 0             |
| yOffset        | yo, y       | The offset on the Y axis                                | 0             |
| zOffset        | zo, z       | The offset on the Z axis                                | 0             |
| targetxoffset  | tx, txo     | Target X-axis offset                                          | 0       |
| targetyoffset  | ty, tyo     | Target Y-axis offset                                          | 0       |
| targetzoffset  | tz, tzo     | Target Z-axis offset                                          | 0       |
| ForwardOffset  | foffset, fo | The Forward offset                                      | 0             |
| Pitch          |             | The pitch rotation                                      | 0             |
| Yaw            |             | The yaw rotation                                        | 0             |
| Roll           |             | The roll rotation                                       | 0             |
| Radius         | r           | The hit radius                                          | 1             |
| Rotation       | rot         | The rotation of the polygon, in the x,y,z format. Same as using pitch/yaw/roll                                                                           | 0,0,0         |
| MatchCasterDirection | matchPlayerDirection, matchDirection, mcd, mpd, md, direction                    | Matches the direction of the polygon to the caster's facing direction                  | true         |
| directiontowardstarget | dtt | Whether the yaw/pitch should be calculated so that the drawn shape aims to the target | false |
| FromOrigin     |             | If the polygon should start in the origin of the metaskill | false      |
| HitConditions  | conditions, cond, c, oC, hC | List of [Inline Conditions](/Skills/Inline-Conditions) that an entity must met to be hit by the polygon mechanic          |<!--type:Conditions-->|

## Examples
```yaml
ExampleSkill:
  Skills:
  - polygon{db=0.25;y=0.1;mpd=false;scale=6;
    oE=[ - effect:particles{p=FLAME} ];
    oP=[ - effect:particles{p=CRIT;a=1;repeat=20;repeati=1} ];
    oS=[ - effect:particles{p=SOUL_FIRE_FLAME} ]
    ;p=10;skip=6;duration=20} @Origin
```
```yaml
ExampleSkill:
  Skills:
  - setVar{var=global.a;v=0}
  - skill{s=[
    - addVar{var=global.a;a=1}
    - polygon{db=0.25;y=0.1;mpd=false;radius=1;scale=6;yaw=<global.var.a>;
      oE=[ - effect:particles{p=FLAME} ];
      oP=[ - effect:particles{p=CRIT;a=1} ];
      oS=[ - effect:particles{p=SOUL_FIRE_FLAME} ]
      ;p=10;skip=2} @Origin
    ];repeat=180;repeati=1}
```


<!--TAGS-->
<!--tag:Meta-Mechanic-->
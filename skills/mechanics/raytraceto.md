## Description
Traces a ray to the target, like the [Raytrace](/skills/mechanics/raytrace) mechanic, but with additional attributes regarding the start and end position of the ray.

> **This is a [Premium-Only] mechanic!**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| startyoffset | syo, ystartoffset, ys | The offset on the y axis of the starting point of the ray | 0   |
| targetyoffset| tyo, ytargetoffset, yt| The offset on the y axis of the ending point of the ray | 0     |
| fromorigin| fo        | If they ray should start from the origin of the mechanic             | false   |
| useeyelocation | uel  | If they ray should start from the eye location of the caster         | false   |
| forwardoffset| startfoffset, sfo | The forward offset of the starting point of the ray       | 0       |
| sideoffset| soffset, sso | The side offset of the starting point of the ray                  | 0       |
| entityskill   | eskill, es | meta-skill to use when the ray hits an entity                   |<!--type:Metaskill-->|
| locationskill | lskill, ls | meta-skill to use when the ray hits a location                  |<!--type:Metaskill-->|
| headshotskill | hsskill, hs | meta-skill to use when it's a headshot                         |<!--type:Metaskill-->|
| maxdistance   | distance, md, d | max distance to trace                                      | 50      |
| raywidth      | rw, w      | Width of the ray traced                                         | 0.2     | 
| ignorepassableblocks | ignorepassable, ip    | ignores collision of passable blocks                                                                          | true          |
| ignoreentities | ignoreentity, ie    | ignores all entities                                                                          | false          |
| fluidcollisionmode   | fcm                   | [Determines the collision behaviour when fluids get hit during ray tracing](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FluidCollisionMode.html) | NEVER<!--type:FluidCollisionMode-->|
| accuracy             | ac, a                 | spread of the traced ray                                                                                                                                 | 1             |
| verticalnoise        | vn                    | vertical spread of the ray                                                                                                                               | 0             |
| horizontalnoise      | hn                    | horizontal spread of the ray                                                                                                                             | 0             |
| raytraceConditions   | rc, rcond, rconditions| Conditions applied to the raytraced target                                                                                                               |<!--type:Conditions-->|
| headshotmultiplier   | hsmultipler, hsm     | headshot power multiplier                                                                                                                                | 1             |


## Examples
```yaml
MyRaytraceToSkill:
  Skills:
  - raytraceto{
      entitySkill=[
        - damage{amount=20}
      ];
      locationSkill=[
        - particles{p=flame;a=20;s=0.2;hS=0.1;vS=0.1}
      ];
      startyoffset=1;
      targetyoffset=1;
      useeyelocation=true
      } @targetlocation ~onUse
```


<!-- LINKS -->
[Premium-Only]: Premium-Features


<!--TAGS-->
<!--tag:Meta-Mechanic-->
<!--tag:Premium-Only-->
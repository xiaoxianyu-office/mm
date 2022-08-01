Mechanic: Raytrace
---------------------

Traces a ray to the target. **[PREMIUM ONLY]**
 
Attributes
----------

| Attribute            | Aliases               | Description                                                                                                                                              | Default Value |
|----------------------|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| entityskill          | eskill, es            | meta-skill to use when the ray hits an entity                                                                                                            |               |
| locationskill        | lskill, ls            | meta-skill to use when the ray hits a location                                                                                                           |               |
| headshotskill        | hskill, hs            | meta-skill to use when it's a headshot                                                                                                                   |               |
| maxdistance          | distance, md, d       | max distance to trace                                                                                                                                    | 50            |
| raywidth             | rw, w                 | Width of the ray traced                                                                                                                                  | 0.2           |      |
| ignorepassableblocks | ignorepassable, ip    | ignores collision of passable blocks                                                                                                                     | true          |
| fluidcollisionmode   | fcm                   | [Determines the collision behaviour when fluids get hit during ray tracing](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/FluidCollisionMode.html) | NEVER         |
| accuracy             | ac, a                 | spread of the traced ray                                                                                                                                 | 1             |
| verticalnoise        | vn                    | vertical spread of the ray                                                                                                                               | 0             |
| horizontalnoise      | hn                    | horizontal spread of the ray                                                                                                                             | 0             |
| raytraceConditions   | rc, rcon, rconditions | Conditions applied to the raytraced target                                                                                                               | NONE          |
| headshotmultiplier   | hsmultiplier, hsm     | headshot power multiplier                                                                                                                                | 1             |

Examples
--------

```
  - raytrace{
      entitySkill=[
        - damage{amount=20}
      ];
      headshotSkill=[
        - effect:particles{particle=reddust;color=#ff0000}
      ];
      locationSkill=[
        - particles{p=flame;a=20;s=0.2;hS=0.1;vS=0.1}
      ];
      raytraceConditions=[
        - samefaction false
      ]} @targetlocation ~onUse
```
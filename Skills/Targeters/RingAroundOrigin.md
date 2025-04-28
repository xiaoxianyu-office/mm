## Description
Targets locations in a specified ring around the origin.

Rotations are in radians, such as 90 degrees of axis rotation being `1.57`.

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |
| points    | p         | The points that make up the ring                                     | 10      |
| rotationx | rotx, rx  | The rotation of the ring on the x axis                               | 0       |
| rotationy | roty, ry  | The rotation of the ring on the y axis                               | 0       |
| rotationz | rotz, rz  | The rotation of the ring on the z axis                               | 0       |
| offsetx   | offx, ox  | The offset of the ring on the x axis                                 | 0       |
| offsety   | offy, oy  | The offset of the ring on the y axis                                 | 0       |
| offsetz   | offz, oz  | The offset of the ring on the z axis                                 | 0       |
| relative  |           | Whether the Ring's orientation should be relative to the caster's    | false   |

## Examples
```yaml
ExampleSkill:
  Skills:
  - projectile{...;
    onEnd=[
      - effect:particles @RingAroundOrigin{r=5;p=15}
    ]}

# This will draw a vertical circle instead of a flat one:
VerticalRingSkill:
  Skills:
  - particles{p=enchanted_hit;a=1;} @RAO{r=2;rz=1.57;p=9;relative=true}
```


## Aliases
- [x] ringOrigin
- [x] RAO
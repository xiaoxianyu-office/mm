## Description
Targets random points in a ring around the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the ring                                               | 5       |
| points    | p         | The number of points to generate                                     | 10      |
| amount    | a         | How many of the generated points should be targeted                  | 1       |
| rotationx | rotx, rx  | The rotation on the x axis                                           | 0       |
| rotationy | roty, ry  | The rotation on the y axis                                           | 0       |
| rotationz | rotz, rz  | The rotation on the z axis                                           | 0       |
| offsetx   | offx, ox  | The offset on the x axis                                             | 0       |
| offsety   | offy, oy  | The offset on the y axis                                             | 0       |
| offsetz   | offz, oz  | The offset on the z axis                                             | 0       |


## Examples
```yaml
  Skills:
  - particle @randomRingPoint{r=4;p=20;a=10}
```
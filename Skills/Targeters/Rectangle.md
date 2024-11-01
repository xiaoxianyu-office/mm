## Description
Returns the # of points target locations that comprise a rectangle. Depending on the parameters, some elements of the rectangle can be modified, such as it being filled or not, if to target only its outline, its location and so on


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| x         |           | The size of the rectangle on the **x** axis                          | 1       |
| y         |           | The size of the rectangle on the **y** axis                          | 1       |
| z         |           | The size of the rectangle on the **z** axis                          | 1       |
| xOffset   |           | The offset of the rectangle on the **x** axis                        | 0       |
| yOffset   |           | The offset of the rectangle on the **y** axis                        | 0       |
| zOffset   |           | The offset of the rectangle on the **z** axis                        | 0       |
| points    | p, density, d | Amount of points per cube 'line'                                 | 10      |
| filled    | fill, f   | If the rectangle should be filled                                    | false   |
| outline   | edge, onlyEdge, e, onlyOutline, o | If only the outline should be drawn          | false   |
| rotation  | r         | The 3D rotation of the rectangle                                     | 0,0,0   |
| fromOrigin| origin    | If the rectangle should be drawn from the origin of the metaskill    | false   |


## Examples
```yaml
ExampleMob1:
  Type: ZOMBIE
  Skills:
  - particle{p=FLAME;a=1} @Rectangle{d=12;f=false;r=45,45,0;yOffset=1.5;outline=true} ~onDamaged

ExampleMob2:
  Type: ZOMBIE
  Skills:
  - particle{p=SOUL_FIRE_FLAME;a=1} @Rectangle{d=12;r=45,45,45;yOffset=3;fill=true} ~onDamaged
```


## Aliases
- [x] cube
- [x] cuboid
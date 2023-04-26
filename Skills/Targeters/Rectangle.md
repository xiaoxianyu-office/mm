## Targeter: Rectangle
Returns the # of points target locations that comprise a rectangle. Depending on the parameters, some elements of the rectangle can be modified, such as it being filled or not, if to target only its outline, its location and so on

### Attributes

| Attribute      | Aliases  | Description                                                | Default |
|----------------|----------|------------------------------------------------------------|:-------:|
| x              |          | The size of the rectangle on the **x** axis                |         |
| y              |          | The size of the rectangle on the **y** axis                |         |
| z              |          | The size of the rectangle on the **z** axis                |         |
| xOffset        |          | The offset of the rectangle on the **x** axis              |         |
| yOffset        |          | The offset of the rectangle on the **y** axis              |         |
| zOffset        |          | The offset of the rectangle on the **z** axis              |         |
| points         | p        | Amount of points per cube 'line'                           |         |
| filled         | fill, f  | If the rectangle should be filled                          |         |
| outline        | edge, onlyEdge, e, onlyOutline, o | If only the outline should be drawn |       |
| rotation       | r        | The 3D rotation of the rectangle                           |         |
| fromOrigin     | origin   | If the rectangle should be drawn from the origin of the metaskill |  |

## Examples
```yaml
ExampleMob1:
  Type: ZOMBIE
  Skills:
  - e:p{p=FLAME;a=1} @Rectangle{d=12;f=false;r=45,45,0;yOffset=1.5;outline=true} ~onDamaged

ExampleMob2:
  Type: ZOMBIE
  Skills:
  - e:p{p=SOUL_FIRE_FLAME;a=1} @Rectangle{d=12;r=45,45,45;yOffset=3;fill=true} ~onDamaged
```
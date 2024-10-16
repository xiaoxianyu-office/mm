## Description
Targets random points in a cone in front of the caster.  
Note: Cone is fixed on the y-axis, and cannot be rotated up or down


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| angle     | a         | The angle of the cone                                                | 90      |
| range     | r         | The length of the cone                                               | 16      |
| points    | p         | The number of points that will be targeted inside the cone  | angle\*range\*0.1|
| slices    | s         | This defines how many layers or subdivisions (slices) the cone is divided into along its length (range).<br>More slices result in a finer resolution                   | floor(`range`) |
| minpoints | mp        | The minimum number of points to be generated for each slice          | 1       |
| rotation  | rot       | The rotation of the cone                                             | 0       |
| yoffset   | yo, y     | The y offset of the cone                                             | 0       |
| exact     | e         | Whether to use a precise method to distribute points uniformly across the cone's surface instead of randomly generating them                                                    | false   | 


## Examples
```yaml
  Skills:
  - effect:particles @Cone{a=45;r=10;p=200}
```
## Description
Returns the # of points target locations that comprise a cone.  
Note: Cone is fixed on the y-axis, and cannot be rotated up or down


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| angle     | a         | The angle of the cone                                                | 90      |
| range     | r         | The length of the cone                                               | 16      |
| points    | p         | The number of points that will be targeted inside the cone    | angle*range*0.1|
| rotation  | rot       | The rotation of the cone                                             | 0       |
| yoffset   | yo, y     | The y offset of the cone                                             | 0       |


## Examples
```yaml
  Skills:
  - effect:particles @Cone{a=45;r=10;p=200}
```
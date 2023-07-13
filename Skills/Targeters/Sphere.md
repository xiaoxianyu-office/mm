## Description
Targets points in a sphere around the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |
| points    | p         | The amount of points                                                 | 10      |
| yoffset   | y         | The offset of the targets on the y axis                              | 0       |

## Examples
```yaml
ExampleSkill:
  Skills:
  - effect:particles @Sphere{r=6;points=50}
```
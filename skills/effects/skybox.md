## Description
Changes the skybox of the target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| skybox    | sky, s, type, t, environment, env, e | What skybox should be shown to the player | 0       |

### Skybox Attribute
| Value | Description |
| ----- | ----------- |
| Any Integer Below 1 | Cancel the modified skybox |
| Any Integer Above 0 | Rainy |


## Examples
Makes every player in a 20 blocks radius see the "rainy" skybox
```yaml
  Skills:
  - skybox{s=1} @PIR{r=20}
```
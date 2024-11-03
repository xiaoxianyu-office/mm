## Description
Targets the locations of all players in a given radius around the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |
| yoffset   | y         | The y offset of the targeted locations                               | 0       |


## Examples
```yaml
  Skills:
  - effect:particles @PlayerLocationsInRadius{r=10}
```


## Aliases
- [x] LocationRadius
- [x] PLIR
- [x] PLR
## Description
Special targeter to target a region. Only works with specific mechanics


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| min       |           | The location of the first point                                      | 0,0,0   |
| max       |           | The location of the second point                                     | 0,0,0   |
| world     |           | The world the region is in                                    | `<caster.l.w>` |


## Examples
```yaml
  Skills:
  - worldEditReplace{from=STONE;to=AIR} @Region{min=0,0,0;max=100,100,100;world=resources}
```
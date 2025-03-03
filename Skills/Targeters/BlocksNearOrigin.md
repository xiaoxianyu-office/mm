## Description
Targets all blocks in a radius around the origin of the metaskill


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 2       |
| radiusy   | ry, yradius, yr | The y component of the radius                                  | radius  |
| shape     | s         | The shape of the selected blocks. Can be `SPHERE`, `CUBE`            | SPHERE<!--type:Shape-->|
| noise     | n         | The randomness of the targeter                                       | 0       |
| noair     | na        | Whether air should not be targeted                                   | true    |
| onlyair   | oa        | Whether only air should be targeted                                  | false   |


## Examples
This skill will target some of the blocks in a 10 blocks radius around the origin of the metaskill

```yaml
ExampleSkill:
  Skills:
  - effect:particles @BlocksNearOrigin{r=10;noise=0.5}
```


## Aliases
- [x] BNO
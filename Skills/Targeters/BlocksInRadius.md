## Description
Targets all blocks in a radius of the inherited targets.


## Attributes 
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 2       |
| radiusy   | ry, yradius, yr | The y component of the radius                                  | radius  |
| shape     | s         | The shape of the selected blocks. Can be `SPHERE`, `CUBE`            | SPHERE<!--type:Shape-->|
| noise     | n         | The randomness of the targeter                                       | 0       |
| noair     | na        | Whether air should not be targeted                                   | true    |
| onlyair   | oa        | Whether only air should be targeted                                  | false   |
| nearorigin| no        | Whether the targeter should target the origin                        | false   |


## Examples

Those metaskills will allow you to target every non air block in a 10 blocks radius around the trigger of the skilltree

```yaml
ExampleSkill1:
  Skills:
  - skill{s=ExampleSkill2} @trigger

ExampleSkill2:
  Skills:
  - effect:particles @BlocksInRadius{r=10}
```


## Aliases
- [x] BIR
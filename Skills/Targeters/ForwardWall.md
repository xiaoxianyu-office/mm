## Description
Targets a plane of blocks in front of the caster


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| forward   | f, amount, a | How distant should the targeted point be                          | 5       |
| yoffset   | y         | The y offset of the plane                                            | 0       |
| height    | h         | The height of the plane                                              | 2       |
| width     | w         | The width of the plane                                               | 3       |


## Examples
```yaml
ExampleSkill:
  Skills:
  - effect:particles @ForwardWall{f=5;y=1;h=2;w=2}
```
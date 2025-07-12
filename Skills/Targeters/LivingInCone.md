## Description
Targets all living entities in cone with a specified angle, length and rotation relative to facing direction


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| angle     | a         | The angle of the cone                                                | 90      |
| range     | r         | The length of the cone                                               | 16      |
| rotation  | rot       | The rotation of the cone                                             | 0       |
| usepitch  | pitch, p  | Whether to generate the cone also depending on the caster's pitch    | false   |
| yoffset   | yo        | The y offset to be added to the generated cone's location            | 0       |
| livingonly | lo       | Whether to target only living entities                               | true    |


## Examples
```yaml
ExampleSkill:
  Skills:
  - ignite @LivingInCone{a=45;r=20}
```


## Aliases
- [x] entitiesInCone
- [x] livingEntitiesInCone
- [x] LEIC
- [x] EIC
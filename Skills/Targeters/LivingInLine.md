## Description
Targets any entities in a line between the inherited target and the casting mob


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The distance between each point in the line and the radius around each point where entities will be targeted                                                                | 1       |
| fromorigin| fo        | If the line should be drawn from the origin of the metaskill         | false   |


## Examples
```yaml
ExampleSkill1:
  Skills:
  - skill{s=ExampleSkill2} @Forward{f=10}

ExampleSkill2:
  Skills:
  - ignite @LivingInLine{r=0.5}
```


## Aliases
- [x] entitiesInLine
- [x] livingEntitiesInLine
- [x] LEIL
- [x] EIL
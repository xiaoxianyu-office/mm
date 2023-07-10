## Description
Targets locations between the mob and the inherited target


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The distance between each point in the line                          | 1       |
| fromorigin| fo        | If the line should be drawn from the origin of the metaskill         | false   |


## Examples
```yaml
ExampleSkill1:
  Skills:
  - skill{s=ExampleSkill2} @Forward{f=10}

ExampleSkill2:
  Skills:
  - effect:particles @Line{r=0.5}
```
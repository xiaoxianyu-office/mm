## Description
Targets all players near the inherited target locations


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |


## Examples
This mechanic will damage every player in a 2 block radius from the target of the mob once executed
```yaml
ExampleSkill1:
  Skills:
  - skill{s=ExampleSkill2} @target

ExampleSkill2:
  Skills:
  - damage{a=10} @PlayersNearTargetLocations{r=2}
```


## Aliases
- [x] playersNearTargetLocation
- [x] PNTL
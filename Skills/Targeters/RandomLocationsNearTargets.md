## Description
Targets random locations near the inherited targets


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of points                                                 | 5       |
| radius    | r, maxradius, maxr | The radius in which target points will be generated         | 5       |
| minradius | minr      | The minimum radius in which target points will be generated          | 0       |
| spacing   | s         | The minimum amount of space between selected targets                 | 0       |
| onsurface | surface   | Whether the selected location should be on a surface that is not air | false   |


## Examples
```yaml
ExampleSkill1:
  Skills:
  - skill{s=ExampleSkill2} @PIR{r=10}

ExampleSkill2:
  Skills:
  - effect:particles @RandomLocationsNearTargets{a=5;r=2}
```


## Aliases
- [x] randomLocationsNearTarget
- [x] randomLocationsNearTargetEntities
- [x] randomLocationsNearTargetLocations
- [x] RLNT
- [x] RLNTE
- [x] RLNTL
## Description
Targets the first solid block below the inherited targets


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| tries     | t, max, m | The maximum number of attempts the targeter will make to fetch the targets | 3 |


## Examples
This mechanic will mask the block below every player in a 10 blocks radius to ice
```yaml
ExampleSkill1:
  Skills:
  - skill{s=ExampleSkill2} @PIR{r=10}

ExampleSkill2:
  Skills:
  - blockmask{r=1;m=ICE} @FloorOfTargets
```


## Aliases
- [x] floorsOfTarget
- [x] FOT
## Description
Targets the location of the inherited targets


## Attributes
>*This targeter has no attributes*


## Examples
```yaml
ExampleSkill1:
  Skills:
  - skills{s=ExampleSkill2} @EIR{r=10}

ExampleSkill2:
  Skills:
  - lightning @LocationsOfTargets
```


## Aliases
- [x] locationOfTarget
- [x] LOT
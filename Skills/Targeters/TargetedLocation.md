## Description
Targets the location of the inherited targeted locations. Useful for [Targets Filtering](/Skills/Metaskills#targets-filtering) by using [Targeter Options](/Skills/Targeters#targeter-options).

## Attributes
>*This targeter has no attributes*


## Examples
```yaml
ExampleSkill1:
  Skills:
  - skills{s=ExampleSkill2} @PlayerLocationsInRadius{r=10}

ExampleSkill2:
  Skills:
  - lightning @PlayerLocationsInRadius{}
```


## Aliases
- [x] targetedLocations
- [x] targetedLoc
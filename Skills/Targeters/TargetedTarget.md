## Description
Targets the inherited targeted entities. Useful for [Targets Filtering](/Skills/Metaskills#targets-filtering) by using [Targeter Options](/Skills/Targeters#targeter-options).


## Attributes
> *This targeter has no attributes*


## Examples
```yaml
ExampleSkill1:
  Skills:
  - skills{s=ExampleSkill2} @PIR{r=10}
```
##
```yaml
ExampleSkill2:
  Skills:
  - lightning @TargetedTarget
```


## Aliases
- [x] targeted
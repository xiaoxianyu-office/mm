## Description
Creates a swirling vortex of smoke at the targeted entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d     | How many intervals the swirl will last                                   | 5       |
| interval  | i     | How many ticks there are between each pulse of smoke                     | 1       |


## Examples
```yaml
SmokeSwirlSkill:
  Skills:
  - smokeswirl{duration=10;interval=10} @TargetLocation
```


## Aliases
- [x] effect:smokeswirl
- [x] e:smokeswirl


<!--TAGS-->
<!--tag:Effect-->

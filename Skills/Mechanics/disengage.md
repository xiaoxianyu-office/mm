## Description
Causes the caster to leap backwards away from the target entity


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| velocity  | v, magnitude | The velocity of the leap                                          | 1       |
| velocityy | yvelocity, vy, yv | The y component of the velocity of the leap                  | 0.01337 |


## Examples
```yaml
ExampleMob:
  Skills:
  - disengage @trigger ~onDamaged
```


<!--TAGS-->
<!--tag:Movement-->
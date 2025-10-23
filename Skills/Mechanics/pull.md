## Description
Pulls all targeted entities towards the caster with a base velocity,
increasing based on the distance of targets from the caster.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| velocity  | v         | The base velocity of the pull                                        | 1       |
| toOrigin  | to        | Wether or not the target should pulled towards the origin of the skill  | false|

### Velocity Attribute

Targets are pulled much faster based on their distance from the caster.
The defined velocity is a "base" velocity, and the skill scales the
velocity based on distance to attempt to pull the entity directly to the
mob if it is possible based on the base velocity.


## Examples
Pulls the target and then all players within 10 blocks to the casting mob.
```yaml
DeathGrip:
  Skills:
  - pull{velocity=10} @target
  - delay 60
  - pull{v=6;to=true} @PIR{r=10}
```


<!--TAGS-->
<!--tag:Movement-->
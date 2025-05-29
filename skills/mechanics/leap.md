## Description
Causes the mob to leap through the air at the target. Leap calculates a
projectile-like trajectory so that the mob will land directly on top of
the target if the velocity is great enough, otherwise the mob will leap
at far as possible towards the target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| velocity  | v         | The max velocity of the leap                                         | 100     |
| noise     | n         | Added variance to where the mob will land                            | 0       |

### Velocity Attribute
Because of the way this skill works, using very high velocity values is
recommended (usually values exceeding 100 work best). Velocity is
calculated differently with this skill than most others.


## Examples
This skill would cause the mob to leap towards the target at high
speeds, then slam into the ground and cause an explosion.
```yaml
CrushingLeap:
  Cooldown: 10
  Skills:
  - leap{velocity=200} @target
  - delay 20
  - jump{velocity=-100}
  - effect:explosion @self
  - damage{amount=20} @EntitiesInRadius{r=5}
```


<!--TAGS-->
<!--tag:Movement-->
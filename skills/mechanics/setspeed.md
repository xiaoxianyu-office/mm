## Description
Causes the target to change its speed attribute

> The [MovementSpeed](/Mobs/Options#movementspeed) option must be explicitly set for this to work!

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed     | a, amount, m, multiplier, s, v, value | Speed multiplier to apply to the base speed of the entity | 1       |
| type      | t         | Type of speed, can be `FLY` or any other string. If not exactly `FLY`, this will change walk speed                                                                              | WALK    |

<!--
This value will then be multiplied by the default speed value of the respective speed type:
- `0.1` for `WALK`
- `0.2` for `FLY`
-->

## Examples
This will set the mob's walking speed to 2 when it spawns
```yaml
  Skills:
  - setspeed{speed=2;type=walking} ~onSpawn
```
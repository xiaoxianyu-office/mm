## Description
Causes the target to change its speed attribute


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| speed     | a, amount, m, multiplier, s, v, value | Speed of the entity                      | 1       |
| type      | t         | Type of speed, can be `FLY` or any other string. If not exactly `FLY`, this will change walk speed                                                                              | WALK    |

### Speed Attribute
This value will then be multiplied by the default speed value of the respective speed type:
- `0.1` for `WALK`
- `0.2` for `FLY`

## Examples
This will set the mob's walking speed to 2 when it spawns
```yaml
  Skills:
  - setspeed{speed=2;type=walking} ~onSpawn
```
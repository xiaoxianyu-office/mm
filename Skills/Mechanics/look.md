## Description
Causes the entity to look at its target. Can be used to make cool effects or creepy ones depending on how creative you get with it.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| headOnly  | ho        | Only the mob's head is facing the target                             | false   |
| force     | f         | Forces the mob to look at the target (even works with no AI)         | false   |
| forcepaper | fp       | Whether to use Paper's method to force the mob to look at the target | false   |
| immediately | immediate, i | Immediately causes the mob to turn towards the target with no turning animation. | true   |
| speed | s, duration, ticks | The amount of ticks the entity will take to fully face towards the new direction | 10 |

## Examples
The skill below causes the mob to immediately force it's head to face
the target immediately. Giving it a creepy effect as only the head will
stare for a short bit before the body catches up and turns around as
well.
```yaml
CreepyStare:
  Skills:
  - look{headOnly=true;immediately=true} @Target
```


<!--TAGS-->
<!--tag:Movement:Rotation-->

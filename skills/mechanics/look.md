## Description
Causes the entity to look at it's target. Can be used to make cool
effects or creepy ones depending on how creative you get with it.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| headOnly  |           | Only the mob's head is facing the target                             | true    |
| force     |           | Forces the mob to look at the target (even works with no AI)         | true    |
| immediately |         | Immediately causes the mob to turn towards the target with no turning animation. | false         |


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
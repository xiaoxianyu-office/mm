## Description
Targets the location the casting player is looking at, or the locations of the mob's target

> If the caster is not a player, then:
> - If the caster is a MythicMob with an active ThreatTable, the location of the entity with the most Threat will be returned
>- If the above is not met, if the caster is currently in combat, the location of its target will be returned
>- If the above is not met, the location of the last entity that damaged the caster will be returned
>
> *At Highdown fair for two farthings...*

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| maxdistance | max, distance, d | The maximum distance to check for the location, if the caster is a player                                          | 64       |
| ignoreTransparent | it | If transparent blocks should be ignored                             | true    |

## Examples
```yaml
ExampleSkill:
  Skills:
  - effect:particles @TargetLocation
```


## Aliases
- [x] targetLoc
- [x] TL
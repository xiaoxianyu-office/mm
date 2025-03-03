## Description
Targets all MythicMobs or vanilla overrides of the given type(s) in a radius around the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |
| types     | type, t   | The type(s) of the target MythicMobs. Can be a list                  |         |
| checkiftemplate | cit | Whether to check against the mob's templates instead of the mob's internal name | false |


## Examples
```yaml
ExampleSkill:
  Skills:
  - ignite @MobsInRadius{r=10;types=IncredibleZombie,SpookyScarySkeleton}
```


## Aliases
- [x] MIR
- [x] mobs
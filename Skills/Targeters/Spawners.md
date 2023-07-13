## Description
Targets the locations of the specified mob spawners


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| spawners  | spawner, s| The names of the spawners. Can be either a simple name, a group (`g:groupname`) or contain wildcards (`Spawner*` to target *Spawner1*,*Spawner2*,*Spawner3*...)                |         |


## Examples
```yaml
ExampleSkill_SingleSpawner:
  Skills:
  - effect:particles @Spawner{s=TestSpawner}
```
```yaml
ExampleSkill_Group:
  Skills:
  - effect:particles @Spawner{s=g:ExampleSpawnerGroup}
```
```yaml
ExampleSkill_WildCard:
  Skills:
  - effect:particles @Spawner{s=ForestSpawner_*}
```
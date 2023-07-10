## Description
Targets the nearest structure of the specified type within a radius in the caster's world


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The type of the structure                                         | STRONGHOLD |
| radius    | r         | The radius of the targeter                                           | 5000    |
| unexplored | u        | Whether the structure should be unexplored                           | false   |


## Examples
```yaml
StrongholdFinder:
  Cooldown: 10
  Skills:
  - projectile{hp=false;se=false;sb=false;v=5;d=100;onTick=[ effect:particles ]} @NearestStructure{r=1000}
```
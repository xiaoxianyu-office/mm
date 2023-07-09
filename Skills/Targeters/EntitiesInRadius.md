## Description
Targets all entities in the given radius around the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the targeter                                           | 5       |
| livingonly| living, l | Whether the targeter should target only living entities              | true    |


## Examples
```yaml
  Skills:
  - ignite @EIR{r=10}
```


## Aliases
- [x] livingEntitiesInRadius  
- [x] livingInRadius  
- [x] allInRadius  
- [x] EIR
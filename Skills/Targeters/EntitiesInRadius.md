## Description
Targets all entities in the given radius around the caster


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| shape     |           | The "shape" in which to fetch entities. Can be any [shape](/Enum/Shape)| SPHERE<!--type:ShapeAdv-->|
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
- [x] entitiesnearby
- [x] nearbyentities
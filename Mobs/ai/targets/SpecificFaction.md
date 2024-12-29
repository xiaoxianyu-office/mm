## Description
Causes the mob to target a specific faction.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| faction | f        | The faction to target |        |


## Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  AITargetSelectors:
    - clear
    - specificfaction{f=somefaction}
```


## Aliases
- [x] nearestspecificfaction
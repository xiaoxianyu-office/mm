## Description
Causes the mob to target monsters of a specific faction.


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
    - specificfactionmonsters{f=somefaction}
```


## Aliases
- [x] nearestspecificfactionmonsters
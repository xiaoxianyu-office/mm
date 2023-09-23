## Description
Checks if the target player's specified material is on cooldown.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | mat, m    | The material to check for                                         | enderpearl |


## Examples
```yaml
  TargetConditions:
  - materialIsOnCooldown{mat=STONE} true
```


## Aliases
- [x] materialCooldown
- [x] matCooldown
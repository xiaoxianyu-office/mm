## Description
Checks the experience points that the target player has.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| level     | l, amount, a | Checks against the experience points missing to reach the next level, in a range from 0 to 1. 0 is "no progress" and 1 is "next level". Accepts ranges.                   | 0       |


## Examples
```yaml
  TargetConditions:
  - enchantingExperience{l=>0.2} true
```

## Aliases
- [x] enchantingExp
- [x] enchantExperience
- [x] enchantExp
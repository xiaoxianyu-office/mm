---
title: StatDamageModifier
---
## Description
Used in stat triggers to check the increased damage (as a multiplier).
Can be useful to differentiate between positive and negative effects.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| value     | v, amount, a, damage, d, multiplier, m | The minimum multiplier to check for. Defaults to 1. Will return true if the multiplier is bigger than the value to check for.  | 1 |


## Examples
```yaml
  Conditions:
  - statDamageModifier{m=1.01) castInstead positiveEffectSkill
  - statDamageModifier{m=0.99) orElseCast negativeEffectSkill
```


## Aliases
- [x] statDamage
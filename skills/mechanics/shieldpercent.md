## Description
Applies an absorb shield to the target entity for a percentage of their
max health.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| multiplier| m         | The multiplier. The value of the shield will be `maxhealth*multiplier` | 0.1   |
| maxabsorb | maxshield, ma, ms | The max value of the shield must not be greater the max health of the mob multiplied by this value                                                      | `Multiplier's value` |


## Examples
Adds shield absorption hearts to caster with a multiplier.
```yaml
  Skills:
  - shieldPercent{multiplier=2;mS=2.5} @self ~onTimer:2000
  - ...
```
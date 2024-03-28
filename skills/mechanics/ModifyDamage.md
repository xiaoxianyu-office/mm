## Description
Modifies the damage event that triggered the skill.  
This mechanic must be synched, meaning that either the mechanic or the initial skill calling it must be run with the `sync=true` attribute


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of the operation                                          | 1       |
| damagetype| type, dt, t | The type of the damage to evaluate                                 | ALL     |
| action    | mod, m    | The [modifier](/Items/Attributes#operations) to use                  | ADDITIVE|


## Examples
```yaml
  Skills:
  - modifyDamage{a=2;modifier=MULTIPLY;sync=true} @self ~onAttack 0.2
```


## Aliases
- [x] modDamage
## Description
Heals the target entity for a percentage of its max-health. Like the
heal skill, can also overheal mobs by a percentage.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| multiplier | m        | The percentage to heal, refers to the targets max-health.<br>0.1 = 10%, 1 = 100% and so on                                                                                      | 0.1     |
| overheal   | oh       | Whether or not to apply overhealing as additional MaxHealth          | false   |

  

## Examples
This will make the casting mob heal for 20% of its health each time it
gets to attack.
```yaml
  Skills:
  - healpercent{m=0.2} @self ~onAttack
```
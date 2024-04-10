## Description
Applies an aura to the target that triggers a skill when they damage
something. Can use any aura attribute


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onattackskill | onattack, oa, onmelee, onhitskill, onhit, oh | [metaskill] to execute if the target hits something   |  |
| cancelEvent | cE, canceldamage | Whether or not to cancel the event that triggered the aura  | false   |
| damageAdd | add, a    | An optional static increase to the original hit's damage             | 0       |
| damageMultiplier | multiplier, m | An optional multiplier to the original hit's damage       | 1       |
| modDamageType | damagetype | The type of the damage inflicted                                |         |
  

## Examples
```yaml
  Skills:
  - onAttack{oH=SuperPunch;cE=true;auraname=MyAura}
```


## Aliases
- [x] onhit
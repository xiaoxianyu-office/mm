## Description
Simulates a physical hit from the mob. Takes melee stats into account (regular skill damage won't unless configured to specifically)
This mechanic shares the same options as the [BaseDamage](https://git.mythiccraft.io/mythiccraft/MythicMobs/-/wikis/skills/mechanics/basedamage) mechanic


## Attributes
| Attribute        | Aliases | Description                         | Default |
|------------------|---------|-------------------------------------|---------|
| multiplier       | m       | The percentage of damage to deal    | 1   |
| ignoreArmor      | ia      | Whether or not to ignore armor      | false   |
| preventknockback | pkb, pk | Whether or not to prevent knockback | false   |
| preventimmunity  | pi      | Whether or not to ignore immunities | false   |

  

## Examples
This example will make the mob deal 150% of its configured melee damage to its
target when its being attacked. Ignoring armors. In this case it would deal 15 damage total since the mob's melee damage is 10.
```yaml
HitMob:
  Type: Zombie
  Damage: 10
  Skills:
    - hit{m=1.5;ia=true} @target ~onDamaged
```
[1] 1 = 100%, 0.5 = 50% and so-on


## Aliases
- [x] physicalDamage
- [x] meleeHit
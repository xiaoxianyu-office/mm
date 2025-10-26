## Description
Simulates a physical hit from the caster. Takes items (including enchantments), melee stats, attribute modifiers, and potion effects into account.  
Inherits every attribute of the [Damage](/skills/mechanics/damage) mechanic.  


## Attributes
| Attribute        | Aliases | Description                         | Default |
|------------------|---------|-------------------------------------|---------|
| multiplier       | m       | The percentage of damage to deal    | 1       |
| forcedDamage     | fd, forced | If this attribute is set, the one specified will be the amount of flat damage that will be inflicted, without consideration for attribute modifiers and similar other modifiers |
| triggerSkills | ts    | Whether the damage mechanic should also be able to trigger `onAttack` related triggers       | true |
| scaleByAttackCooldown | sbac | Whether to scale the damage by the weapon's attack cooldown | false |
> This mechanic inherits every attribute of the [Damage](/skills/mechanics/damage) mechanic
>> - The `amount` attribute is ignored
>> - The `triggerSkills` attribute is **defaulted** at `true`
>> - The `damagecause` attribute is **set** at `ENTITY_ATTACK`
>> - The `tags` attribute will always have a `melee` tag.


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


## Aliases
- [x] physicalDamage
- [x] meleeHit


<!--TAGS-->
<!--tag:Damage-->
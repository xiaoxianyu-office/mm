## Description
Damages the target entity for a percentage of the mob's damage.  
Inherits every attribute of the [Damage](/skills/mechanics/damage) mechanic.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| multiplier       | m       | The percentage of damage to deal                                | 1       |
| useAttribute | attribute, attr | Whether the damage should use the real entity's attack attribute, instead of its raw base damage                                                                 | false   | 
> This mechanic inherits every attribute of the [Damage](/skills/mechanics/damage) mechanic
>> The `amout` attribute is ignored


## Examples
This example will make the mob deal 150% of its original damage to its
target when its being attacked. In this case it would deal 15 damage,
since the mob's base-damage is 10.
```yaml
AMob:
  Type: HUSK
  Damage: 10
  Skills:
  - basedamage{m=1.5} @target ~onDamaged
```


## Aliases
- [x] bd
- [x] weaponDamage
- [x] wd


<!--TAGS-->
<!--tag:Damage-->
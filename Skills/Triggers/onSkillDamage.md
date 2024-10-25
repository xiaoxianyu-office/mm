## Description
Executes the skill when the mob deals damage to other entities via a mechanic.  

> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that was damaged


## Examples
```yaml
ExampleMob:
  Type: 
  Skills:
  - damage @PIR{r=10} ~onTimer:20
  - message{m="Get damaged! MUHAHAHA"} @trigger ~onSkillDamage
```


## Aliases
- [x] onSkillHit
- [x] onSkill_Damage
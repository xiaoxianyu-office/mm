## Description
Executes a skill when the mob's projectile hits an entity.

> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that has been hit

| [Implemented Placeholders](/Skills/Placeholders#variable-placeholders)     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |
| `<skill.var.damage-cause>`     |


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onBowHit)


## Examples
```yaml
NotYourAverageSkeleton:
  Type: SKELETON
  Equipment:
    - BOW HAND
  Skills:
  - modifyDamage{a=3;modifier=MULTIPLY;sync=true} ~onBowHit
```


## Aliases
- [x] onBow_Hit
- [x] onArrowHit
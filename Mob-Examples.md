## Hostile Mobs

_todo_

## Neutral Mobs

### The Adventurer

A simple mob that protects the land, attacking hostile mobs with an iron sword, speaks randomly, defends himself against attackers, and celebrates his victories.

---

```yaml
Adventurer:
  Type: zombie
  Display: 'Adventurer'
  Damage: 6
  Health: 65
  Faction: good
  Disguise: Player Refreshin setCustomName Adventurer setCustomNameVisible true
  AIGoalSelectors:
  - 0 clear
  - 1 meleeattack
  - 2 lookatplayers
  - 3 randomstroll
  - 3 float
  AITargetSelectors:
  - 0 clear
  - 1 attacker
  - 2 otherfactionmonsters
  Equipment:
  - IRON_SWORD HAND
  Options:
    PreventSunburn: true
    AlwaysShowName: false
    PreventOtherDrops: true
    PreventMobKillDrops: true
    MovementSpeed: 0.26
    Silent: true
  Skills:
  - effect:sound{s=entity.villager.yes;v=.6;p=0.7} @self ~onTimer:60 0.6
  - effect:sound{s=entity.villager.yes;v=.6;p=0.7} @self ~onKill
  - effect:sound{s=entity.villager.hurt;v=.6;p=0.7} @self ~onDamaged
  Drops:
  - IRON_SWORD 1
```

## Passive Mobs

_todo_
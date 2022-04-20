## Hostile Mobs

### The Sentinel

A fast and dangerous miniboss that makes horrific sounds, has particles, wears a command block for a head, and uses a Netherite Sword to defeat anything in it's way. 

```yaml
Sentinel:
  Type: wither_skeleton
  Display: 'Sentinel'
  Damage: 10
  Health: 120
  Faction: bad
  AIGoalSelectors:
  - 0 clear
  - 1 meleeattack
  - 2 lookatplayers
  - 3 randomstroll
  AITargetSelectors:
  - 0 clear
  - 1 players
  - 2 attacker
  - 3 otherfaction
  Modules:
    ThreatTable: true
  Options:
    PreventSunburn: true
    AlwaysShowName: false
    PreventOtherDrops: true
    PreventMobKillDrops: true
    MovementSpeed: 0.45
    Silent: true
  Equipment:
  - COMMAND_BLOCK HEAD
  - NETHERITE_SWORD HAND
  Skills:
  - effect:sound{s=entity.enderman.scream;v=1;p=0.2} @self ~onDeath
  - effect:sound{s=entity.enderman.hurt;v=1;p=0.2} @self ~onDamaged
  - effect:sound{s=entity.enderman.stare;v=.2;p=0.2} @self 0.5 ~onTimer:150
  - effect:particles{particle=spell;amount=50;hS=1;vS=1;speed=5} @self ~onTimer:2 0.8
  - throw{velocity=8;velocityY=4} @EIR{r=4} ~onDamaged 0.2
```

## Neutral Mobs

### The Adventurer

A simple mob that protects the land, attacking hostile mobs with an iron sword, speaks randomly, defends himself against attackers, and celebrates his victories.

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
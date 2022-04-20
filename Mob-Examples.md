## Hostile Mobs

### The Demon

The Demon is hostile to players, those who attack it, and any MythicMob within the "good" faction. It is also equipped with a Netherite Axe, has flame particles, and can hover and shoot fireballs (due to it using the blaze as the base mob!) It uses a custom skin that requires [Disguises](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Mobs/Disguises).

```yaml
Demon:
  Type: blaze
  Display: 'Demon'
  Damage: 6
  Health: 60
  Faction: bad
  Disguise: Player 164_ setCustomName Demon setCustomNameVisible false
  AIGoalSelectors:
  - 0 meleeattack
  - 2 randomstroll
  - 3 float
  AITargetSelectors:
  - 0 clear
  - 1 players
  - 2 attacker
  - 3 specificfaction good
  Equipment:
  - NETHERITE_AXE HAND
  Options:
    AlwaysShowName: false
    PreventOtherDrops: true
    PreventMobKillDrops: true
    MovementSpeed: 0.35
    Silent: false
  Skills:
  - Flames @self ~onTimer:100
  - effect:sound{s=entity.elder_guardian.death;v=1;p=0.7} @self ~onDeath
  - effect:sound{s=entity.blaze.death;v=0.3;p=0.7} @self ~onDeath
  - effect:sound{s=entity.elder_guardian.ambient;v=1;p=2} @self 0.5 ~onTimer:150
  - effect:sound{s=entity.elder_guardian.hurt;v=1;p=0.7} @self ~onDamaged
```

---

### The Sentinel

A fast and dangerous miniboss that makes horrific sounds, has particles, wears a command block for a head, and uses a Netherite Sword to defeat anything in its way. 

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

A simple mob that protects the land, attacking hostile mobs with an Iron Sword, speaks randomly, defends himself against attackers, and celebrates his victories. It uses a custom skin that requires [Disguises](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Mobs/Disguises).

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
  - effect:sound{s=entity.villager.ambient;v=.6;p=0.7} @self ~onTimer:60 0.6
  - effect:sound{s=entity.villager.yes;v=.6;p=0.7} @self ~onKill
  - effect:sound{s=entity.villager.hurt;v=.6;p=0.7} @self ~onDamaged
  Drops:
  - IRON_SWORD 1
```

## Passive Mobs

### The Civilian

Civilians are docile NPC mobs that don't like to fight. They will run from combat and talk to players when they right-click them. They will also pick up professions like a normal villager. It uses a custom skin that requires [Disguises](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Mobs/Disguises). It also uses AIGoalSelectors that require [Mythicmobs Premium](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Premium-Features).

```yaml
Citizen:
  Type: VILLAGER
  Display: 'Civilian'
  Damage: 6
  Health: 20
  Faction: good
  Disguise: Player Refreshin setCustomName Civilian setCustomNameVisible true
  AIGoalSelectors:
  - 0 fleeConditional{distance=15;speed=1;safespeed=1;conditions=[ - incombat true ]}
  AITargetSelectors:
  - 0 clear
  - 1 attacker
  Modules:
    ThreatTable: false
  Options:
    PreventItemPickup: false
    AlwaysShowName: false
    Despawn: true
    PreventOtherDrops: true
    PreventMobKillDrops: true
    MovementSpeed: 0.35
    Silent: true
  Skills:
  - effect:sound{s=entity.villager.yes;v=.6;p=0.8} @self ~onInteract
  - effect:sound{s=entity.villager.hurt;v=.6;p=0.8} @self ~onDamaged
  - effect:sound{s=entity.villager.death;v=.6;p=0.8} @self ~onDeath
  Drops:
  - BREAD 1-3 0.4
  - CARROT 1-3 0.4
  - BEETROOT 1-3 0.4
  - POTATO 1-3 0.4
  - EMERALD 1-2 0.1
  - GOLD_NUGGET 1-6 0.2
  - DIAMOND 1 0.01
```
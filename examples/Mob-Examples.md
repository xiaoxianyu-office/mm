## Hostile Mobs

### Demon
The Demon is hostile to players, those who attack it, and any MythicMob within the "good" faction. It is also equipped with a Netherite Axe, has flame particles, and can hover and shoot fireballs (due to it using the blaze as the base mob!) It uses a custom skin that requires [Disguises](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Mobs/Disguises).

Difficulty: `⭐⭐⭐` (Medium)
<details>
  <summary>Step-by-step Tutorial</summary>
  
### Tutorial
Let's add some basic options to the mob:
```yml
Demon:
  Type: blaze # Mob Type
  Display: 'Demon' # Mob Display name
  Damage: 6 # The amount of Damage it deals
  Health: 60 # The amount of Health it has
  Faction: bad # Set the Demon's faction as "bad".
  Disguise: Player 164_ setCustomName Demon setCustomNameVisible false # Disguise it as a player with a skin. Requires LibsDisguises.
```

Then, let's give it some custom AI to prevent it from attacking unwanted entities:

```yml
  # ...
  AIGoalSelectors:  # We will not clear the mob's base AI, instead adding to it
  - meleeattack # Uses melee attacks
  - randomstroll # Randomly walks
  - float # floats on water
  AITargetSelectors:
  - clear # Clears the mob's base AI
  - players # Firstly targets players
  - attacker # Targets whatever attacks it
  - specificfaction good # Targets mobs from the faction "good"
```

Let's give the mob an axe:

```yml
  # ...
  Equipment:
  - NETHERITE_AXE HAND # Makes the mob hold a netherite axe in its hand
```

Now, we further customize the mob a bit:

1. Let's make the mob not always show its name.
2. Then, let's prevent vanilla blaze drops from dropping when the mob dies.
3. Furthermore, let's prevent mobs the blaze kills from dropping their loot.
4. Let's set the mob's movement speed to `0.35`.
5. Let's make the mob have sounds.
   
What we end up with is this:

```yml
  # ...
  Options:
    AlwaysShowName: false # Don't always show name unless hovered
    PreventOtherDrops: true # Don't drop default blaze drops on death
    PreventMobKillDrops: true # Prevent mobs that the demon kills from dropping loot
    MovementSpeed: 0.35 # Sets movement speed
    Silent: false # Play the default blaze sound effects
```

Finally, let's make the mob more interesting by adding some abilities to it.

```yml
  # ...
  Skills:
  # PARTICLE EFFECTS
  - effect:flames @self ~onTimer:100 # Every 100 ticks (5 seconds), show a spawner flame effect on mob's location.
  # SOUND EFFECTS
  - effect:sound{s=entity.elder_guardian.ambient;v=1;p=2} @self 0.5 ~onTimer:150 # Every 150 ticks (7.5 seconds), 50% chance to play the entity.elder_guardian.ambient sound with volume 1 and pitch 2
  - effect:sound{s=entity.elder_guardian.hurt;v=1;p=0.7} @self ~onDamaged # When the mob gets damaged, play the entity.elder_guardian.hurt sound with volume 1 and pitch 0.7
  - effect:sound{s=entity.elder_guardian.death;v=1;p=0.7} @self ~onDeath # When the mob dies, play the entity.elder_guardian.death sound with volume 1 and pitch 0.7
  - effect:sound{s=entity.blaze.death;v=0.3;p=0.7} @self ~onDeath # When the mob dies, also play the entity.blaze.death sound with volume 0.3 and pitch 0.7
```

These skills essentially add custom sounds and effects to the mob, which really brings it to life.
</details>

<details>
  <summary>End Product</summary>

```yml
Demon:
  Type: blaze # Mob Type
  Display: 'Demon' # Mob Display name
  Damage: 6 # The amount of Damage it deals
  Health: 60 # The amount of Health it has
  Faction: bad # Set the Demon's faction as "bad".
  Disguise: Player 164_ setCustomName Demon setCustomNameVisible false # Disguise it as a player with a skin. Requires LibsDisguises.
  AIGoalSelectors:  # We will not clear the mob's base AI, instead adding to it
  - meleeattack # Uses melee attacks
  - randomstroll # Randomly walks
  - float # Randomly floats
  AITargetSelectors:
  - clear # Clears the mob's base AI
  - players # Firstly targets players
  - attacker # Targets whatever attacks it
  - specificfaction good # Targets mobs from the faction "good"
  Equipment:
  - NETHERITE_AXE HAND # Makes the mob hold a netherite axe in its hand
  Options:
    AlwaysShowName: false
    PreventOtherDrops: true
    PreventMobKillDrops: true
    MovementSpeed: 0.35
    Silent: false
  Skills:
  # PARTICLE EFFECTS
  - effect:flames @self ~onTimer:100 # Every 100 ticks (5 seconds), show a spawner flame effect on mob's location.
  # SOUND EFFECTS
  - effect:sound{s=entity.elder_guardian.ambient;v=1;p=2} @self 0.5 ~onTimer:150 # Ever 150 ticks (7.5 seconds), 50% chance to play the entity.elder_guardian.ambient sound with volume 1 and pitch 2
  - effect:sound{s=entity.elder_guardian.hurt;v=1;p=0.7} @self ~onDamaged # When the mob gets damaged, play the entity.elder_guardian.hurt sound with volume 1 and pitch 0.7
  - effect:sound{s=entity.elder_guardian.death;v=1;p=0.7} @self ~onDeath # When the mob dies, play the entity.elder_guardian.death sound with volume 1 and pitch 0.7
  - effect:sound{s=entity.blaze.death;v=0.3;p=0.7} @self ~onDeath # When the mob dies, also play the entity.blaze.death sound with volume 0.3 and pitch 0.7
```
</details>

---

### The Sentinel

A fast and dangerous miniboss that makes horrific sounds, has particles, wears a command block for a head, and uses a Netherite Sword to defeat anything in its way. 

```yaml
Sentinel:
  Type: wither_skeleton # Base mob wither skeleton. Keep note that this means that when the mob attacks other entities, they will receive the WITHER effect.
  Display: 'Sentinel' # The name of the mob.
  Damage: 10 # Deals 10 damage on hit
  Health: 120 # Has 120 HP.
  Faction: bad # Sets the mob to be in the faction 'bad'
  AIGoalSelectors: # What's the mob going to do?
  - clear # Clears the mob's AI
  - meleeattack # Melee-attacks its targets
  - lookatplayers # Looks at players.
  - randomstroll # Randomly walks around when off-combat.
  AITargetSelectors:
  - clear # Clears the mob's AI
  - players # Targets players
  - attacker # Then targets whatever attacks it
  - otherfaction # Targets whatever is not in the 'bad' faction
  Options: # Additional mob options
    PreventSunburn: true # Prevents the mob from burning in daylight
    AlwaysShowName: false # Prevents the mob from showing its name all the time. (Players will have to look at the mob to show the name)
    PreventOtherDrops: true # Prevents vanilla wither skeleton drops.
    PreventMobKillDrops: true # Prevents mobs that the Sentinel kills from dropping loot.
    MovementSpeed: 0.45 # Fast movement speed.
    Silent: true # Disables its default sounds. Useful if you are going to use custom sounds.
  Equipment: # Things that the mob will wear.
  - COMMAND_BLOCK HEAD # Wears a Command Block on its head.
  - NETHERITE_SWORD HAND # Holds a Netherite Sword in its hand
  Skills:
  # SOUNDS
  - effect:sound{s=entity.enderman.scream;v=1;p=0.2} @self ~onDeath
  - effect:sound{s=entity.enderman.hurt;v=1;p=0.2} @self ~onDamaged
  - effect:sound{s=entity.enderman.stare;v=.2;p=0.2} @self ~onTimer:150 0.5
  # PARTICLES
  - effect:particles{particle=spell;amount=50;hS=1;vS=1;speed=5} @self ~onTimer:2 0.8
  # ABILITIES
  - throw{velocity=8;velocityY=4} @EIR{r=4} ~onDamaged 0.2 # When damaged, the mob has a 20% chance to launch nearby players in a radius of 4.
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
  - clear
  - meleeattack
  - lookatplayers
  - randomstroll
  - float
  AITargetSelectors:
  - clear
  - attacker
  - otherfactionmonsters
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
  - fleeConditional{distance=15;speed=1;safespeed=1;conditions=[ - incombat true ]}
  AITargetSelectors:
  - clear
  - attacker
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
MythicMobs is based all around customized entities/mobs and there are
plenty of options, attributes that you can utilize. Below you find a
complete list of options/attributes that can be added to your custom
creations.

Most of the options below are optional, meaning you don't have to configure the entire
list every time you are creating a new mob. All that really is required
are the `Internal_Name` and the `Type`.

Table Of Contents:

[[_TOC_]]

Breaking Down The Mob Configuration
-------------------------

#### Internal_Name
This string will be how your mob will be referenced internally in MythicMobs and can be any name you like.
Must be a unique name and does not clash with other internal mob names, **NO SPACES ALLOWED**.
```yml
example_name:
```

#### Type
This field determines which entity type your creation will be based upon.
A complete list of available [entity types] can be found on spigot javadocs.\
**Note: Several mob options for new entity types that Minecraft adds to the base game will not function until Mythic adds support for said entity types.**
```yml
example_mob:
  Type: zombie
```
```yml
another_mob:
  Type: ZOMBIE
```

#### Display
Sets the display name of the mob.
This option supports color codes and [placeholders].
**The mob's name will not change or update on its own, you have to use [setname] mechanic to change or update it.**
```yml
example_mob:
  Type: zombie
  Display: Example Mob
```
```yml
example_mob:
  Type: zombie
  Display: Example Mob <caster.hp> <red><&heart></red>
```

#### Health
Sets the base value of the mob's max health attribute.
Mythic doesn't have any limitations on max health but Spigot, however, caps the max health at `2048`.
This can easily be changed in spigot's configuration file, `server_root\spigot.yml`.
Whenever the mob is holding or wearing an item with attribute modifiers will also affect the total max health.
```yml
example_mob:
  Type: zombie
  Display: Example Mob
  Health: 30
```

#### Damage
Sets the base value of the mob's attack damage attribute.
1 damage equals to 0.5 hearts, so a mob with 6 damage will deal 3 full hearts of damage.
This attribute will never affect damage done by ranged attacks, like arrows or potions.
Whenever the mob is holding or wearing an item with attribute modifiers will also affect the mob's melee damage.
```yml
example_mob:
  Type: zombie
  Display: Example Mob
  Damage: 20
```

#### Armor
Sets the base value of the mob's armor attribute. Minecraft caps the max armor value to 30.
Whenever the mob is holding or wearing an item with attribute modifiers will also affect the total armor.
```yml
example_mob:
  Type: zombie
  Display: Tanker
  Armor: 25
```

#### HealthBar
Creates a basic health bar hologram. Requires "Holograms" or "HolographicDisplays" plugin.
```yml
example_mob:
  Type: zombie
  Display: HealthyBoi
  Health: 1000
  HealthBar:
    Enabled: true
    Offset: 1.45
```

#### BossBar
Defines and controls the health bar of the mob.
Looks like the Ender Dragon's or the Wither's health bar, but is configurable in appearance.
See [BossBar](Mobs/BossBar)
```yml
example_mob:
  Type: zombie
  Armor: 25
  BossBar:
    Enabled: true
    Title: Tanker
    Range: 20
    Color: RED
    Style: NOTCHED_6
    CreateFog: true
    DarkenSky: true
    PlayMusic: true
```

#### Faction
Sets the mob's faction, which can be used for advanced [Custom AI] configurations or [targeter filtering].
Must be alphanumeric and is case-sensitive.
```yml
example_mob:
  Type: zombie
  Armor: 25
  Faction: Tank
```

#### Mount
Sets the mount of your mob, must be another MythicMob.
The mob will automatically ride on the defined mount when it spawns.
```yml
another_example:
  Type: chicken
  Mount: example_mo
```

#### Options
This is a special field which comes with numerous sub-options, like determining if the mob should despawn,
setting knockback resistance, follow range, movement speed and many more.
A list of available mob options can be found in the [Mob Options](Mobs/Options) page
```yml
slow_persistent_mob:
  Type: husk
  Options:
    MovementSpeed: 0.025
    Despawn: PERSISTENT
```

#### Modules
This field allows you to enable or disable modules, like [Threat Tables] and/or [Immunity Tables]
```yml
example_mob:
  Type: husk
  Modules:
    ThreatTables: false
    ImmunityTables: false
```

#### AIGoalSelectors
Modifies and customizes the [AI goals] of the mob.
```yml
dummy_mob:
  Type: zombie
  AIGoalSelectors:
    - clear
```
```yml
passive_mob:
  Type: zombie
  AIGoalSelectors:
    - clear
    - randomstroll
    - randomlookaround
```

#### AITargetSelectors
Modifies and customizes the [AI targets] of the mob.
```yml
neutral_mob:
  Type: zombie
  AIGoalSelectors:
    - clear
    - meleeattack
    - randomstroll
    - randomlookaround
  AITargetSelectors:
    - clear
    - attacker
```

#### Drops
Add or completely modify the mob loot drops.
Can be vanilla items, mythic items, experience points, cross-plugin items (if supported), or even custom drop tables with their own condition system.
See [Drops & DropTables](drops/Drops) for more information.
```yml
example_mob:
  Type: zombie
  Options:
    PreventOtherDrops: true
  Drops:
    - diamond 32 1
    - netherite_ingot 12 0.5
```

#### DamageModifiers
Modifies how much damage the mob will take from different damage causes.
For example, DamageModifiers can be used to make the mob immune to melee attacks, but weak to ranged attacks.
See [Damage Modifiers](Mobs/DamageModifiers) for more information.
```yml
example_mob:
  Type: zombie
  DamageModifiers:
    - ENTITY_ATTACK 0
    - PROJECTILE 1.25
```

#### Equipment
Equips the mob with vanilla items or mythic items when it first spawns.
See [Equipment](Mobs/Equipment) for more information.
```yml
example_mob:
  Type: zombie
  Options:
    PreventRandomEquipment: true
  Equipment:
    - diamond_sword HAND
    - diamond_helmet{name=<green>COMMON</green> helmet} HEAD
```

#### KillMessages
Customize the [kill messages] that appears when the mob kills a player.
```yml
example_mob:
  Type: zombie
  Display: Tanker
  KillMessages:
    - <caster.name> yeeted <target.name>!!
    - You're too weak <target.name>!!
```

#### LevelModifiers
MythicMobs can have [levels](Mobs/Levels) and this field is used to determine which kinds of statistics they should gain on when their levels change.
```yml
example_mob:
  Type: zombie
  Display: Dummy
  LevelModifiers:
    Damage: 2
    Health: 0.25
```

#### Disguise
Changes the appearance of the mob to be like other entity types.
Requires the plugin [LibsDisguises](https://www.spigotmc.org/resources/libs-disguises-free.81/) to be installed and functioning on your server.
See [Add-on: Disguises](Mobs/Disguises) for more information.
```yml
#This mob acts like a zombie but looks like a chicken
example_mob:
  Type: zombie
  Disguise: chicken
```

#### Skills
Skills are an integral feature of Mythic. All mobs are able to have skills of various types that can be triggered under different circumstances with varying
conditions. The Mythic skill system is quite intuitive once you get used to it, and can be used to create anything from simple mobs to incredibly complex bosses.
See [Skills](Skills/Skills) to get started on making your own skills.
```yml
#swaps locations with the player that right-clicked the mob
example_mob:
  Type: zombie
  Skills:
    - swap{} @trigger ~onInteract
```

#### Trades
Customizes the villager trades.
Villagers must have a profession and a profession level of 2 to be able to keep its custom trades.

```yml
MerchantTest:
  Type: VILLAGER
  Display: '&6Merchant Test'
  Options:
    Profession: CLERIC
    Type: DESERT
    Level: 2
  Trades:
    1:
      Item1: 5 EMERALD
      Item2: 5 DIAMOND
      Result: DIAMOND_SWORD
      MaxUses: 5
    2:
      Item1: 64 EMERALD
      Result: mmoitems.SWORD.CUTLASS
      MaxUses: 1
    3:
      Item1: 32 EMERALD
      Item2: 1 PAPER
      Result: 1 CUSTOM_ITEM
      MaxUses: 1
```

Examples
-----------------------------

More mobs examples can be found in the [Examples](examples/Common-Examples#mobs) section.
<!--  ONLY NEED TO LINK USERS TO EXAMPLES SECTION
Please keep in mind that you in no way have to use all of these mob
options and that this is an advanced example designed to show the
possibilities. All that you need to apply is whatever you want for you
mob. The only required options/attributes are the internal-mobname and a
mob-type. After that it's completely up to you.
```
    super_zombie:
     Type: zombie
     Display: '&lSuper Zombie&r'
     Health: 200
     Damage: 14
     Armor: 10
     Faction: superb_zombies
     Mount: super_zombie_undead_horse
     Options:
      PreventOtherDrops: true
      PreventItemPickup: true
      Despawn: false
      KnockbackResistance: 0.25
      MovementSpeed: 0.25
     Modules:
      ThreatTable: false
      ImmunityTable: true
     AIGoalSelectors:
     - clear
     - meleeattack
     - randomstroll
     AITargetSelectors:
     - clear
     - attacker
     - players
     Drops:
     - diamond 1-3 1
     - exp 50 1
     - super_zombie_sword 1 1
     DamageModifiers:
     - ENTITY_ATTACK 0
     - PROJECTILE 1.25
     - MAGIC 1.75
     Equipment:
     - super_zombie_helmet:4
     - super_zombie_sword:0
     KillMessages:
     - '<target.name> was superbly slain by a <mob.name>'
     LevelModifiers:
       MovementSpeed: 0.01
       KnockbackResistance: 0.05
       Health: 2
       Damage: 1
     Disguise: player ashijin setDisguiseName &6MythicMobs<&sq>s<&spGod
     Skills:
     - throw{v=5;vy=5} @rigger ~onAttack 0.5
     - sound{s=entity.zombie.hurt;v=1;p=0} ~onDamaged
     - e:particles{p=cloud;a=50;s=0.05} ~onDeath
```
-->
[entity types]: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/EntityType.html
[setname]: Skills/mechanics/setname
[placeholders]: Skills/Placeholders
[targeter filtering]: Skills/Targeters#targeter-options
[Custom AI]: Mobs/Custom-AI
[Threat Tables]: Mobs/ThreatTables
[Immunity Tables]: Mobs/ImmunityTables
[AI goals]: /Mobs/Custom-AI#ai-goal-selectors
[AI targets]: /Mobs/Custom-AI#ai-target-selectors
[kill messages]: Mobs/KillMessages
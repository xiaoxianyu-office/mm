Triggers are used to determine how a skill is triggered from within the
mobs skill configuration section.

<u>**TRIGGERS CANNOT BE USED IN META-SKILLS AND SHOULD NOT BE INCLUDED
IN THEM.**</u> 

Triggers can only be used *to activate* the meta-skill
itself (in the mob's configuration file).

> Each trigger starts with a `on` string. That string is **case sensitive**, so make sure to write it correctly or the trigger will not work

## Using Triggers
Triggers are defined in the skill section of the mob configuration and
must use a tilde (~) in front of them. In the case of the Timer, a time
in ticks is also required.
```yml
SkeletalWizard_Fire:
  Type: WITHER_SKELETON
  Display: '&Skeletal Fire Wizard'
  Health: 50
  Damage: 0.5
  Skills:
  - ignite{ticks=100} @target ~onAttack
  - skill{s=FireShield} @trigger ~onDamaged 0.1
  - skill{s=AOEFire} ~onTimer:300
```

In this example the mob will also set its target on fire when
melee-attacking, will use a "FireShield" skill when taking damage, and
will use the "AOEFire" skill every 300 ticks, or every 15 seconds.

## Not using Triggers...
Skill triggers give far more flexibility in determining exactly when a
skill should go off. It is **highly** recommended that you trigger all
your skills using advanced triggers as opposed to the old, legacy
methods.

If a skill does not have a trigger, it will default to the `~onCombat`
trigger which will execute when these events occur:
- When the mob deals or takes damage
- When the mob spawns
- When the mob dies

```yml
SkeletalWarrior:
  Mobtype: skeleton
  Display: '<blue>A Skeletal Warrior</blue>'
  Skills:
  - skill{s=Bash} =10%-90%
```
In this instance the Bash skill is triggered when the mob deals or takes
damage when it is between 10% and 90% health.


# The @trigger Targeter

You may have noticed there is an [`@trigger`](/Skills/Targeters/Trigger) targeter in the examples
shown above, and listed in the [targeters](/Skills/Targeters) section. The `@trigger` will target the
entity that "caused" the skill to trigger, i.e. when a player damages a mob and
that mob has an ~onDamaged skill, it will target that player.
If a signal is being sent to a mob, it will target the mob that sent
the signal, and so on.


# Additional Triggers
Links to triggers added by addon plugins. Any triggers from these links will not work without that plugin installed.

- [Mythic Crucible](https://git.mythiccraft.io/mythiccraft/mythiccrucible/-/wikis/Skills/Triggers)
- [Mythic Enchantments](https://git.mythiccraft.io/mythiccraft/mythicenchants/-/wikis/Skills/Triggers)


# Triggers 
**Table of all available triggers:**
| Trigger                                | When it fires...                                              |
|----------------------------------------|---------------------------------------------------------------|
| [onCombat](/Skills/Triggers/onCombat)  | Default                                                       |
| [onAttack](/Skills/Triggers/onattack)   | When the mob hits something                                  |
| [onDamaged](/Skills/Triggers/ondamaged) | When the mob is damaged                                      |
| [onSpawn](/Skills/Triggers/onspawn)     | When the mob spawns                                          |
| [onDespawn](/Skills/Triggers/ondespawn) | When the mob is despawned                                    |
| [onReady](/Skills/Triggers/onready) | Triggered the first time a mob is spawned from a spawner     |
| [onLoad](/Skills/Triggers/onload)       | When the mob is loaded after a server restart                |
| [onSpawnOrLoad](/Skills/Triggers/onspawnorload) | When the mob either [spawns](/Skills/Triggers/onspawn) or [loads](/Skills/Triggers/onload)   |
| [onDeath](/Skills/Triggers/ondeath)     | When the mob dies                                            |
| [onTimer](/Skills/Triggers/onTimer) | Every \# ticks (where \# is the interval in ticks)           |
| [onInteract](/Skills/Triggers/oninteract) | When the mob is right-clicked                                |
| [onPlayerKill](/Skills/Triggers/onplayerkill) | When the mob kills a player                                  |
| [onEnterCombat](/Skills/Triggers/onentercombat) | When the mob enters combat (requires threat tables be on)    |
| [onDropCombat](/Skills/Triggers/ondropcombat) | When the mob leaves combat (requires threat tables be on)    |
| [onChangeTarget](/Skills/Triggers/onchangetarget) | When the mob changes targets (requires threat tables be on)  |
| [onExplode](/Skills/Triggers/onexplode) | When the mob explodes (typically only used for creepers)     |
| [onPrime](/Skills/Triggers/onprime)     | When the creeper charges up for an explosion                 |
| [onCreeperCharge](/Skills/Triggers/oncreepercharge) | When the creeper is charged (when lightning hits a creeper)  |
| [onTeleport](/Skills/Triggers/onteleport) | When the mob teleports (typically only used for endermen)    |
| [onSignal](/Skills/Triggers/onsignal) | When the mob receives a signal                               |
| [onShoot](/Skills/Triggers/onshoot)     | When the mob fires a projectile                              |
| [onBowHit](/Skills/Triggers/onbowhit)   | When the mob's fired projectile hits an entity               |
| [onTame](/Skills/Triggers/ontame)       | When the mob gets tamed                                      |
| [onBreed](/Skills/Triggers/onbreed)     | When the mob breeds with another mob.                        |
| [onTrade](/Skills/Triggers/ontrade)     | When the Villager completes a trade. Requires Paper          |
| [onChangeWorld](/Skills/Triggers/onchangeworld) | When the mob changes world                                   |
| [onBucket](/Skills/Triggers/onbucket)   |When the cow is milked or an entity is bucketed (axolotl etc.)|
| [onSkillDamage](/Skills/Triggers/onskilldamage) | When the mob deals damage to other entities via a mechanic   |
| [onHear](/Skills/Triggers/onhear)       | When the mob hears a sound, [if enabled](/Mobs/Mobs#hearing) |
| [onProjectileHit](/Skills/Triggers/onProjectileHit) | When a mob's special projectile hits an entity   |
| [onProjectileLand](/Skills/Triggers/onProjectileLand) | When a mob's special projectile hits a block   |
| [onDismounted](/Skills/Triggers/onDismounted) | When the mob is dismounted from |

<!-- LINKS -->
[ThreatTables]: /Mobs/ThreatTables
[@trigger]: /Skills/Targeters/Trigger
[@origin]: /Skills/Targeters/Origin
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders
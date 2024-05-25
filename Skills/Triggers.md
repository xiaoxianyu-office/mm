Triggers are used to determine how a skill is triggered from within the
mobs skill configuration section.

<u>**TRIGGERS CANNOT BE USED IN META-SKILLS AND SHOULD NOT BE INCLUDED
IN THEM.**</u> 

Triggers can only be used *to activate* the meta-skill
itself (in the mob's configuration file).


# Additional Triggers
Links to triggers added by addon plugins. Any triggers from these links will not work without that plugin installed.

- [Mythic Crucible](https://git.mythiccraft.io/mythiccraft/mythiccrucible/-/wikis/Skills/Triggers)
- [Mythic Enchantments](https://git.mythiccraft.io/mythiccraft/mythicenchants/-/wikis/Skills/Triggers)


# Triggers 
**Table of all available triggers:**
| Trigger                                | When it fires...                                             |
|----------------------------------------|--------------------------------------------------------------|
| onCombat                               | Default                                                      |
| [onAttack](#onattack)                  | When the mob hits something                                  |
| [onDamaged](#ondamaged)                | When the mob is damaged                                      |
| [onSpawn](#onspawn)                    | When the mob spawns                                          |
| [onDespawn](#ondespawn)                | When the mob is despawned                                    |
| [onReady / onFirstSpawn](#onready)                    | Triggered the first time a mob is spawned from a spawner     |
| [onLoad](#onload)                      | When the mob is loaded (spawning or loading after a restart) |
| [onDeath](#ondeath)                    | When the mob dies                                            |
| [onTimer:*#*](#ontimerticks)           | Every \# ticks (where \# is the interval in ticks)           |
| [onInteract](#oninteract)              | When the mob is right-clicked                                |
| [onPlayerKill](#onplayerkill)          | When the mob kills a player                                  |
| [onEnterCombat](#onentercombat)        | When the mob enters combat (requires threat tables be on)    |
| [onDropCombat](#ondropcombat)          | When the mob leaves combat (requires threat tables be on)    |
| [onChangeTarget](#onchangetarget)      | When the mob changes targets (requires threat tables be on)  |
| [onExplode](#onexplode)                | When the mob explodes (typically only used for creepers)     |
| [onPrime](#onprime)                    | When the creeper charges up for an explosion                 |
| [onCreeperCharge](#oncreepercharge)    | When the creeper is charged (when lightning hits a creeper)  |
| [onTeleport](#onteleport)              | When the mob teleports (typically only used for endermen)    |
| [onSignal:*[signal]*](#onsignalsignal) | When the mob receives a signal                               |
| [onShoot](#onshoot)                    | When the mob fires a projectile                              |
| [onBowHit](#onbowhit)                  | When the mob's fired projectile hits an entity               |
| [onTame](#ontame)                      | When the mob gets tamed                                      |
| [onBreed](#onbreed)                    | When the mob breeds with another mob.                        |
| [onTrade](#ontrade)                    | When the Villager completes a trade. Requires Paper          |
| [onChangeWorld](#onchangeworld)        | When the mob changes world                                   |
| [onBucket](#onbucket)                  | When the cow is milked or an entity is bucketed (axolotl etc.)             |
| [onSkillDamage](#onskilldamage)        | When the mob deals damage to other entities via a mechanic   |
| [onHear](#onhear)                      | When the mob hears a sound, [if enabled](/Mobs/Mobs#hearing) |

<!--
ADD THIS TRIGGER BACK WHEN IT WORKS

| onKill                       | When something kills a mob                                   |
-->

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

You may have noticed there is an `@trigger` targeter in the examples
shown above, and listed in the [targeters](/Skills/Targeters) section. The `@trigger` will target the
entity that "caused" the skill to trigger, i.e. when a player damages a mob and
that mob has an ~onDamaged skill, it will target that player.
If a signal is being sent to a mob, it will target the mob that sent
the signal, and so on.

# All Available Triggers
#### ~onSpawn
Executes the skill when the mob spawns.  
> There is no associated [@trigger]
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob spawns
    - message{m=SPAWN} @World ~onSpawn
```

#### ~onDeath
Executes the skill when the mob dies.  
If the server is a Paper one, it is possible to cancel the death event as long as the cancelevent mechanic is synched. The health that the mob has after this is based on what is specified in the `ReviveHealth` Option.  
> The associated [@trigger] is the entity that killed the caster
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob dies
    - message{m=DEATH} @World ~onDeath
```
```yaml
ImmortalCow:
  Type: COW
  Display: '&eImmortal Cow'
  Health: 20
  Options:
    ReviveHealth: -1
  Skills:
  - skill{s=[
    - cancelevent
    - e:p{p=HEART;hs=0.5;vs=0.5;y=1.5}
    - speak{m=Call an ambulance, but not for me!}
    ];sync=true} @self ~onDeath
```
#### ~onAttack
Executes the skill when the mob attacks an entity.
> The associated [@trigger] is the entity that was attacked
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Damage: 1
  Skills:
    # sends a message to all the players in the world
    # when the mob attacks an entity
    - message{m=ATTACK} @World ~onAttack
```

#### ~onDamaged
Executes the skill when the mob takes damage.
> The associated [@trigger] is the entity that dealt the damage

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.damage-amount>`    |
| `<skill.var.damage-type>`      |

```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob takes damage
    - message{m=DAMAGED} @World ~onDamaged
```

#### ~onDespawn
Executes the skill when the mob despawns.
> The associated [@trigger] is the caster itself
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob takes damage
    - message{m=DESPAWNED} @World ~onDespawn
```

#### ~onExplode
Executes the skill when the mob explodes.  
`mobGriefing` gamerule must be set to true for this to work.  
Generally, this trigger only works with creepers and TNTs since other mobs tend to not explode...  
> There is no associated [@trigger]
```yml
EXAMPLE_MOB:
  Type: CREEPER
  Skills:
    # sends a message to all the players in the world
    # when the mob explodes
    - message{m=EXPLODE} @World ~onExplode
```

#### ~onTeleport
Executes the skill when the mob teleports.  
> There is no associated [@trigger]
```yml
EXAMPLE_MOB:
  Type: ENDERMAN
  Skills:
    # sends a message to all the players in the world
    # when the mob teleports
    - message{m=TELEPORT} @World ~onTeleport
```

#### ~onTimer:[tick(s)]
Executes the skill every *n<sup>th</sup>* ticks. Ticks can't be zero and 20 ticks is equal to 1 second.
> Care must be taken when using this trigger as it can lead to server/client performance issues!
>i.e. large amounts of particle effects can cause client lag, or can kick the client from the server

> There is no associated [@trigger].
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world every 0.05 seconds
    - message{m=TIMER every tick (0.05 seconds)} @World ~onTimer:1
    # sends a message to all the players in the world every 2 seconds
    - message{m=TIMER every 40 ticks (2 seconds)} @World ~onTimer:40
```

#### ~onPlayerKill
Executes the skill when the mob kills a player.  
> The associated [@trigger] is the player that has been killed
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob kills a player
    - message{m=PLAYER KILLED} @World ~onPlayerKill
```

#### ~onEnterCombat
Executes the skill when the mob enters combat. **REQUIRES [ThreatTables] to be enabled**  
> The associated [@trigger] is the entity that made the caster enter combat
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Modules:
    ThreatTable: true
  Skills:
    # sends a message to all the players in the world
    # when the mob enters combat
    - message{m=ENTERED COMBAT} @World ~onEnterCombat
```

#### ~onDropCombat
Executes the skill when the mob drops combat. **REQUIRES [ThreatTables] to be enabled**  
> There is no associated [@trigger]
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Modules:
    ThreatTable: true
  Skills:
    # sends a message to all the players in the world
    # when the mob enters combat
    - message{m=DROPPED COMBAT} @World ~onDropCombat
```

#### ~onChangeTarget
Executes the skill when the mob changes target. **REQUIRES [ThreatTables] to be enabled**
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Modules:
    ThreatTable: true
  Skills:
    # sends a message to all the players in the world
    # when the mob's target changes
    - message{m=Target Changed} @World ~onChangeTarget
```

#### ~onInteract
Executes the skill when a player interacts with, or *right-clicks*, the mob.  
> The associated [@trigger] is the player that interacted with the caster
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when a player right-clicks the mob
    - message{m=INTERACTED} @World ~onInteract
```

#### ~onSignal:[signal]
Executes the skill when the mob receives a signal from the [signal](/Skills/mechanics/signal) mechanic.  
A signal must be alphanumeric.  
> The associated [@trigger] is the entity that sent the signal
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a signal to all mythicmob entity in a radius of 64 blocks
    # when a player right-clicks the mob
    - signal{s=MOO_FOR_ME} @EIR{r=64} ~onInteract
```

```yml
DUMMY_MOB:
  Type: COW
  Skills:
    # sends a message to all the players in the world
    # when the mob receives a "MOO_FOR_ME" signal
    - message{m=MOO} @World ~onSignal:MOO_FOR_ME
```

You may also choose to not specify a signal for this trigger, in which case the associated mechanic will be triggered every time the mob receives a generic signal.
```yml
DUMMY_MOB:
  Type: COW
  Skills:
    # sends a message to all the players in the world
    # when the mob receives a signal
    - message{m=MOO...?} @World ~onSignal
```


#### ~onShoot
Executes the skill when the mob shoots a projectile.
For example, skeletons with bows will shoot arrows; ghasts, blazes, or ender dragon will shoot some type of fireball.  
> The associated [@trigger] is the caster
```yml
EXAMPLE_MOB:
  Type: SKELETON
  Skills:
    # sends a message to all the players in the world
    # when the skeleton shoots from a bow
    - message{m=I SHOT AN ARROW} @World ~onShoot
```

#### ~onBowHit
Executes a skill when the mob's projectile hits an entity.
> The associated [@trigger] is the entity that has been hit
```yaml
NotYourAverageSkeleton:
  Type: SKELETON
  Equipment:
    - BOW HAND
  Skills:
  - modifyDamage{a=3;modifier=MULTIPLY;sync=true} ~onBowHit
```

#### ~onBreed
Executes the skill when the mob breeds with another mob.
> This trigger has `@Father` and `@Mother` targeters.
> The associated [@trigger] is the player that made the caster breed
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob breeds
    - message{m=LET'S GET THIS BREAD} @World ~onBreed
```

#### ~onTame
Executes the skill when the player tames the mob.  
> The associated [@trigger] is the player that tamed the mob
```yml
EXAMPLE_MOB:
  Type: WOLF
  Skills:
    # sends a message to all the players in the world
    # when a player tames the mob
    - message{m=I GOT TAMED} @World ~onTame
```

#### ~onCreeperCharge
Executes the skill when the casting creeper is charged.  
> The associated [@trigger] is the caster itself
```yml
EXAMPLE_MOB:
  Type: CREEPER
  Skills:
    # sends a message to all the players in the world
    # when the mob gets charge
    - message{m=CHARGED} @World ~onCreeperCharge
```

#### ~onPrime
Executes the skill when the mob, must be a creeper, is primed (i.e. via the use of a flint and steel).  
> The associated [@trigger] is the caster itself
```yml
EXAMPLE_MOB:
  Type: CREEPER
  Skills:
    # sends a message to all the players in the world
    # when the mob is primed
    - message{m=OOO I'M GONNA EXPLODE} @World ~onPrime
```

#### ~onTrade
Executes the skill when the villager trades with a player.  
> The associated [@trigger] is the player that traded with the villager
```yml
EXAMPLE_MOB:
  Type: VILLAGER
  Skills:
    # sends a message to all the players in the world
    # when the mob's target changes
    - message{m=TRADED} @World ~onTrade
```

#### ~onReady
Executes the skill when the mob is ready to spawn from a [spawner](Spawners)
```yml
EXAMPLE_MOB:
  Type: VILLAGER
  Skills:
    # sends a message to all the players in the world
    # when the mob is about to spawn from a spawner
    - message{m=READY TO SPAWN FROM A SPAWNER} @World ~onReady
    - message{m=READY TO SPAWN FROM A SPAWNER} @World ~onFirstSpawn
```

#### ~onLoad
Executes the skill when the mob is loaded after a server restart.
```yml
EXAMPLE_MOB:
  Type: VILLAGER
  Skills:
    # sends a message to all the players in the world
    # when the mob is loaded after a server restart
    - message{m=LOADED} @World ~onLoad
```

#### ~onChangeWorld
Executes the skill when the mob changes world.
```yaml
WorldJumper:
  Type: WITHER_SKELETON
  Skills:
  - command{c=say The End!} @self ~onChangeWorld ?varEquals{var=skill.world;value=world_the_end}
  - command{c=say The Nether!} @self ~onChangeWorld ?varEquals{var=skill.world;value=world_nether}
```

#### ~onBucket 
Executes the skill when the cow is milked or when an entity is stored in a bucket (axolotl and the other bucketable ones).  
> The associated [@trigger] is the caster itself
```yaml
ANormalCow:
  Type: Cow
  Skills:
  - skill{s=[
    - message{m="HOW DARE YOU?!?"} @trigger
    - sound{s=entity.creeper.primed}
    - explosion{yield=5;delay=30}
    ];cd=2} @self ~onMilk
```

#### ~onSkillDamage
Executes the skill when the mob deals damage to other entities via a mechanic.  
> The associated [@trigger] is the entity that was damaged
```yaml
ExampleMob:
  Type: 
  Skills:
  - damage @PIR{r=10} ~onTimer:20
  - message{m="Get damaged! MUHAHAHA"} @trigger ~onSkillDamage
```

#### ~onHear
Executes the skill when the mob hears a sound, [if this feature has been enabled](/Mobs/Mobs#hearing).  
The `<skill.var.volume>`[placeholder](/Skills/Placeholders#variable-placeholders) can be used in the triggered skill to return a float value between 1 and 15 representing the intensity of the sound (1=quiet footstep, 15=explosion).  

> The associated [@trigger] is the entity that generated the sound  

> The associated [@origin] is the location where the sound was generated  

| [Implemented Placeholders]     |
|--------------------------------|
| `<skill.var.volume>`           |
| `<skill.var.sound-type>`       |

```yaml
ICanHearYou:
  Type: ZOMBIE
  Hearing:
    Enabled: true
  Skills:
  - message{m="I can hear you <trigger.name>! <skill.var.volume>? Way too loud!"} @trigger
```


<!-- LINKS -->
[ThreatTables]: /Mobs/ThreatTables
[@trigger]: /Skills/Targeters/Trigger
[@origin]: /Skills/Targeters/Origin
[Implemented Placeholders]: /Skills/Placeholders#variable-placeholders
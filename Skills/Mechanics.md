Skill Mechanics
===============

Skill Mechanics (or base skills) are simple skills that are built into
MythicMobs. You can call these basic skills by themselves in your mob's
Skill List, or you can create your own meta-skill by combining these
mechanics together.

Some Mechanics are able to target Entities, Locations, or both! Some
don't target anything. You control what your skill targets using a
[Targeter][].

Learn about the new Skill Parameter system added in MM 4.12 [here!][]

Mechanics
---------

These skills usually target entities (players or other mobs), but some
are able to target locations as well.

| Mechanic               | Description                                                    |
|------------------------|----------------------------------------------------------------|
| [Activate Spawner][]   | Activates a MythicMobs spawner at the targeted location        |
| [Animate ArmorStand][] | Animates an armorstand                                         |
| [Arrow Volley][]       | Fires a volley of arrows                                       |
| [Aura Remove][]         | Removes an aura from the target entity                         |
| [Bar Create][]          | Creates a custom boss bar on the casting mob                   |
| [Bar Remove][]          | Removes a custom boss bar on the casting mob                   |
| [Bar Set][]             | Modifies a custom boss bar on the casting mob                  |
| [Break Block][]         | Breaks the block at the target location                        |
| [Break Block And Give Item][] | Breaks the block at the target location and gives an item/droptable |
| [Close Inventory][]    | Closes the target player's inventory                           |
| [Command][]            | Executes a command for each target                             |
| [Consume][]            | Deals damage and restores health per target hit                |
| [Consume Slot][]       | Remove an item from a specific slot of the player's inventory  |
| [Disengage][]          | Causes the caster to leap backwards away from the target entity                               |
| [Disguise][]           | Changes the caster's disguise                                  |
| [Disguise Target][]     | Changes the target's disguise                                  |
| [Undisguise][]         | Remove the caster's disguise                                   |
| [Dismount][]           | Makes the caster dismount whatever they're riding              |
| [Clear Threat][]        | Makes a mob clear its threat table                             |
| [Currency Give][]      | Give money to a player. Requires Vault and a currency plugin   |
| [Currency Take][]      | Take money from a player. Requires Vault and a currency plugin |
| [Damage][]             | Damages the target for an amount                               |
| [Base Damage][]         | Damages the target for a percent of the mob's damage stat      |
| [Damage Percent][]     | Damages the target for a percent of their health               |
| [Disguise As Block][] | |
| [Decapitate][]         | Drops a player head item based on target                       |
| [Doppleganger][]       | Copies the appearance of the target player                     |
| [Drop Item][]           | Drops an item or droptable at the target location              |
| [Eject Passenger][]    | Ejects anything riding the caster                              |
| [Equip][]                | Causes the casting mob to equip an item                                     |
| [Explosion][]            | Causes an explosion                                                         |
| [Extinguish][]           | Removes fire ticks from the target entity                                   |
| [Fawe Paste][]            | Pastes a Schematic using FAWE (Fast Async World Edit)                       |
| [Feed][]                 | Feeds the target player                                                     |
| [Fill Chest][]            | Fills a chest with items, or a droptable                                    |
| [Fly][]                  | Applies an [aura][] that allows the targeted player to fly                           |
| [Force Pull][]           | Teleports the target to the caster                                          |
| [Freeze][]               | Freezes the target for the given number of ticks using the Powdered Snow freezing effect                                                    |
| [Glow][]                 | Makes the target glow                                                       |
| [Give Item][]            | Gives an item to the target                                                 |
| [Give Item From Slot][] | Gives an item to the target from the item in the given slot of caster |
| [GoTo][]                | Move toward the location of the targeter (entity or location) |
| [Heal][]                 | Heals the target                                                            |
| [Heal Percent][]          | Heals the target for a percentage of its max-health                         |
| [Hide From Players][] | Hides the caster, if the caster is a player, from other players for a set duration. |
| [Hologram][] | Summons a hologram to the targeted location                                             |
| [Ignite][]               | Sets the target on fire                                                     |
| [JSON Message][]         | Sends a JSON-format message to the target player(s)                         |
| [Jump][]                 | Causes the caster to jump                                                   |
| [Leap][]                 | Causes the caster to leap towards the target                                |
| [Lightning][]            | Strikes lightning at the target                                             |
| [Look][]                 | Causes the caster to look at the target                                     |
| [Lunge][]                | Causes the caster to lunge forward at the target                            |
| [Message][]              | Sends a message to the target player(s)                                     |
| [Modify Global Score][]  | Modifies a scoreboard value of the fake player: \_\_GLOBAL\_\_                  |
| [Modify Target Score][]  | Modifies a scoreboard value of the target                                   |
| [Modify Score][]         | Modifies the score of a dummy player                                        |
| [Mount][]                | Summons a mob for the caster and mounts it                                  |
| [Mount Me][]             | Forces the targeted entity to mount the caster                                |
| [Mount Target][]         | Mounts the target                                                           |
| [Oxygen][]               | Gives oxygen to a player target                                             |
| [PlayBlockBreakSound][] | Plays a block breaking sound                                                |
| [PlayBlockFallSound][]  | Plays a block falling sound                                                 |
| [PlayBlockHitSound][]   | Plays a block hit sound                                                     |
| [PlayBlockPlaceSound][] | Plays a block place sound                                                   |
| [PlayBlockStepSound][] | Plays a block step sound                                                     |
| [Pose ArmorStand][]       | Changes the pose of the target ArmorStand                                   |
| [Potion][]               | Applies a potion effect to the target                                       |
| [Potion Clear][]          | Removes all potion effects from target entity                               |
| [Prison][]               | Imprisons the target inside a block                                         |
| [Pull][]                 | Pulls the target towards the mob                                            |
| [Push Button][]           | Pushes a button at the target location                                      
| [Ray Trace][]             | Traces a straight line to the target                                        |
| [Ray Trace To][]           | Executes a skill with the result of a raytrace to the target location       |
| [Rally][]                | Causes other nearby mobs to attack the target                               |
| [Random Message][]       | Sends a random message to the target player                                 |
| [Remount][]              | Remounts the mob the caster originally spawned riding, if it is still alive |
| [Remove][]               | Removes the target mob                                                      |
| [Remove HeldItem][]       | Removes some of the item the target player is holding                       |
| [Remove Owner][]          | Removes the ownership of the target mob                                     |
| [Run AI Goal Selector][] | Change the target's AIGoalSelectors                                         |
| [Run AI Target Selector][] | Change the target's AITargetSelectors                                     |
| [Send Action Message][]    | Sends an Actionbar Message to the target player                           |
| [Send Resource Pack][]     | Sends a Resource Pack to the target player                                |
| [Send Title Message][]     | Sends a Title/Subtitle Message to the target player                       |
| [Send Toast][]             | Sends an achievement toast to the target player                           |
| [Set AI][]                 | Disables/enables the AI of the target mob                                 |
| [Set Block Type][]         | Change block type at target location                                      |
| [Set Game Mode][]          | Sets the Game Mode of the target player                                   |
| [Set Gliding][]            | Makes the target glide if they have elytra                                |
| [Set Global Score][]       | Sets a scoreboard value on the fake player: \_\_GLOBAL\_\_                    |
| [Set Gravity][]            | Sets whether gravity affects the target entity                            |
| [Set Health][]             | Sets the health of the target entity                                      |
| [Set Level][]              | Changes the casting mob's level                                           |
| [Set Max Health][]         | Sets the max health of the target entity                                  |
| [Set Mob Color][]          | Changes the color of the target if it is a colorable mob                  |
| [Set Mob Score][]          | Sets a scoreboard value on the casting mob                                |
| [Set Name][]               | Changes the target entity's name                                          |
| [Set NoDamageTicks][]      | Sets the nodamageticks of the target                                      |
| [Set Owner][]              | Makes the target the owner of the casting mob                             |
| [Set Rotation][]           | Sets the rotation of the target                                           |
| [Set Target Score][]       | Sets the score of the target                                              |
| [Set Score][]              | Sets the scoreboard value of a dummy player                               |
| [Set Speed][]              | Sets the target entity's speed attribute                                  |
| [Set Stance][]             | Sets the stance of the target mob                                         |
| [Shield][]                 | Applies an absorb shield to the target entity                             |
| [Shield Break][]           | Forces the player to lower their shield and puts it on cooldown           |
| [Shield Percent][]          | Applies an absorb shield to the target entity for a percentage of their max health |
| [Shoot Fireball][]         | Shoots a fireball at the target                                           |
| [Shoot Potion][]           | Throws a potion at the target                                             |
| [Shoot Skull][]            | Shoots a wither skull at the target                                       |
| [Shoot Shulker Bullet][]   | Shoots a shulker bullet at the target entity                              |
| [Signal][]                 | Sends a signal to a mob                                                   |
| [Speak][]                  | Causes the mob to speak in chat, with options for speech bubbles          |
| [Spring][]                 | Creates a temporary spring of liquid at the target                        |
| [Stun][]                   | Stuns the target entity                                                   |
| [Suicide][]      | Causes the caster to die                                                            |
| [Summon][]       | Summons other mobs at the target                                                    |
| [Swap][]         | Swaps locations with the target                                                     |
| [Add Tag][]      | Adds a scoreboard tag to the target                                                 |
| [Remove Tag][]   | Removes a scoreboard tag from the target                                            |
| [Take Item][]    | Removes an item from the targeted player's inventory                                         |
| [Teleport][]     | Teleports to the target                                                             |
| [Teleport In][]   | Teleports the target relative to the caster's yaw                                   |
| [Teleport To][]   | Teleports the target to a specified location                                        |
| [Threat][]       | Modifies the mob's threat towards the target                                        |
| [Throw][]        | Throws the target entity                                                            |
| [Toggle Lever][] | Toggles a lever at the target location                                              |
| [Toggle Sitting][] | Toggles the sitting state for cats, dogs, foxes, and parrots.                   |
| [Track Location][] | Sets the mob's tracked location to the targeted location |
| [Velocity][]     | Modifies the velocity of the target entity(s)                                       |
| [Weather][]      | Modifies the weather in the target world                                            |
| [Wolf Sit][]      | Forces a targeted wolf to sit.                                               |

Effect Mechanics
----------------

Effects are mechanics that add special effects to your skills. They have
their own page!

[View the list of Effect Mechanics by clicking here][]

Advanced/Meta Mechanics
-----------------------

These skill mechanics have special advanced functions, and most are used
to call other skills. If you specify a target, all other skills called
by these will "inherit" the targets (if applicable).

| Mechanic            | Description                                                                             |
|---------------------|-----------------------------------------------------------------------------------------|
| **[Skill][]**       | Executes a meta-skill. The butter for your bread.                                       |
| [Aura][]            | Applies an aura to the targeted entity, allowing for skills to be run onStart/onTick/onEnd/Etc which all originate from the target. |
| [Cancel Event][]     | Cancel the Event that triggered the current skill-tree. Only works for certain triggers.                                  |
| [Cast][]            | "Casts" a meta-skill using various advanced options.                                     |
| [Chain][]           | Chains a skill between multiple targets that are near each other.                       |
| [Chain Missile][]    | A missile that chains between entities. **Premium-Only** mechanic!                |
| [Delay][]           | Delays execution of the current skill list by a set number of ticks.                                              |
| [Global Cooldown][] | Sets the caster's Global Cooldown timer                                                 |
| [Missile][]         | Fires a homing projectile towards the target.                                                      |
| [Modify Projectile][] | Modifying the projectile / missile / orbital                                   |
| [On Attack][]        | Applies an [aura][] to the target that triggers skills when they attack                 |
| [On Damaged][]       | Applies an [aura][] to the target that triggers skills when they take damage            |
| [On Shoot][]         | Applies an [aura][] to the target that triggers skills when they shoot a bow            |
| [On Block Break][] | Applies an [aura][] to the target that triggers skills when they break a block |
| [On Block Place][] | Applies an [aura][] to the target that triggers skills when they place a block |
| [On Swing][] | Applies an [aura][] to the target that triggers skills when they swing / left click |
| [On Interact][] | Applies an [aura][] to the target that triggers skills when they interact / right click while holding a block or looking at an outlined block (NOT AIR) |
| [On Jump][] | Applies an [aura][] to the target that triggers a skill when they jump (PAPER ONLY MECHANIC) |
| [On Death][] | Applies an [aura][] to the target that triggers a skill when they die |
| [Orbital][]         | Applies an [aura][] that causes a projectile to orbit around the target                 |
| [Projectile][]      | Fires a highly-customizable projectile towards the target                               |
| [Shoot][]           | Shoots a item-projectile at the target, similar to arrows/eggs/snowballs.                                                  |
| [Volley][]            | Shoots a volley of projectile-items at the target with various options |
| [Sudo Skill][]         | Makes the target execute a skill                                       |
| [Random Skill][]      | Executes a random skill from a list                                    |
| [Totem][]             | Creates a static "totem" at a location that can execute other skills        |
| [Variable Add][]      | Adds an amount to a numeric variable                                   |
| [Variable Math][]     | Performs math on a numeric variable                                    |
| [Set Variable][]      | Sets the value of a variable                                           |
| [Variable Unset][]    | Unsets the variable                                                    |
| [Variable Subtract][] | Subtracts an amount from a numeric variable                            |

Universal Attributes
--------------------

The following attributes are applicable to all mechanics.

| Attribute      | Shorthand | Description                                    | Default |
|----------------|-----------|------------------------------------------------|---------|
| cooldown       | cd        | In seconds. Allows for decimal values.         | 0       |
| delay          |           | Delays the execution of the mechanic by a set number of ticks.          | 0       |
| repeat         |           | How many times the mechanic should be repeated | 0       |
| repeatInterval |           | How many ticks must elapse between repetitions | 0       |

Upcoming Mechanics
------------------

These mechanics are currently being worked on and will be in future
releases of the plugin. Some mechanics listed here are already included,
but not yet ready for use.

| Mechanic           | Description                     |
|--------------------|---------------------------------|
| [Time][]           | Changes the time                |


  [here!]: /skills/skillparametersystem
  [Targeter]: /skills/targeters/
  [Activate Spawner]: /skills/mechanics/activatespawner
  [Animate ArmorStand]: /skills/mechanics/animatearmorstand
  [Arrow Volley]: /skills/mechanics/arrowvolley
  [Aura Remove]: /skills/mechanics/auraremove
  [Bar Create]: /skills/mechanics/barcreate
  [Bar Set]: /skills/mechanics/barset
  [Bar Remove]: /skills/mechanics/barremove
  [Break Block]: /skills/mechanics/breakblock
  [Break Block And Give Item]: /skills/mechanics/breakBlockAndGiveItem
  [Close Inventory]: /skills/mechanics/closeinventory
  [Command]: /skills/mechanics/command
  [Consume]: /skills/mechanics/consume
  [Consume Slot]: /skills/mechanics/consumeslot
  [Disengage]: /skills/mechanics/disengage
  [Disguise]: /skills/mechanics/disguise
  [Disguise Target]: /skills/mechanics/disguisetarget
  [Undisguise]: /skills/mechanics/undisguise
  [Dismount]: /skills/mechanics/dismount
  [Clear Threat]: /skills/mechanics/clearthreat
  [Currency Give]: /skills/mechanics/currencygive
  [Currency Take]: /skills/mechanics/currencytake
  [Damage]: /skills/mechanics/damage
  [Base Damage]: /skills/mechanics/basedamage
  [Damage Percent]: /skills/mechanics/percentdamage
  [Decapitate]: /skills/mechanics/decapitate
  [Doppleganger]: /skills/mechanics/doppleganger
  [Drop Item]: /skills/mechanics/dropitem
  [Eject Passenger]: /skills/mechanics/ejectpassenger
  [Equip]: /skills/mechanics/equip
  [Explosion]: /skills/mechanics/explosion
  [Extinguish]: /skills/mechanics/extinguish
  [Fawe Paste]: /skills/mechanics/fawepaste
  [Feed]: /skills/mechanics/feed
  [Fill Chest]: /skills/mechanics/fillChest
  [Fly]: /skills/mechanics/fly
  [Freeze]: /skills/mechanics/freeze
  [aura]: /skills/mechanics/aura
  [Force Pull]: /skills/mechanics/forcepull
  [Glow]: /skills/mechanics/glow
  [Give Item]: /skills/mechanics/giveitem
  [Give Item From Target]: /skills/mechanics/giveitemfromtarget
  [GoTo]: /skills/mechanics/goto
  [Heal]: /skills/mechanics/heal
  [Heal Percent]: /skills/mechanics/healpercent
  [Hologram]: /skills/mechanics/hologram
  [Ignite]: /skills/mechanics/ignite
  [JSON Message]: /skills/mechanics/jsonmessage
  [Jump]: /skills/mechanics/jump
  [Leap]: /skills/mechanics/leap
  [Lightning]: /skills/mechanics/lightning
  [Look]: /skills/mechanics/look
  [Lunge]: /skills/mechanics/lunge
  [Message]: /skills/mechanics/message
  [Modify Global Score]: /skills/mechanics/modifyglobalscore
  [Modify Target Score]: /skills/mechanics/modifytargetscore
  [Modify Score]: /skills/mechanics/modifyscore
  [Mount]: /skills/mechanics/mount
  [Mount Me]: /skills/mechanics/mountme
  [Mount Target]: /skills/mechanics/mounttarget
  [Oxygen]: /skills/mechanics/oxygen
  [Pose ArmorStand]: /skills/mechanics/posearmorstand
  [Potion]: /skills/mechanics/potion
  [Potion Clear]: /skills/mechanics/potionclear
  [Prison]: /skills/mechanics/prison
  [Pull]: /skills/mechanics/pull
  [Push Button]: /skills/mechanics/pushbutton
  [Rally]: /skills/mechanics/rally
  [Random Message]: /skills/mechanics/randommessage
  [Ray Trace]: /skills/mechanics/raytrace
  [Ray Trace To]: /skills/mechanics/raytraceto
  [Remount]: /skills/mechanics/remount
  [Remove]: /skills/mechanics/remove
  [Remove HeldItem]: /skills/mechanics/removehelditem
  [Remove Owner]: /skills/mechanics/removeowner
  [Run AI Goal Selector]: /skills/mechanics/runaigoalselector
  [Run AI Target Selector]: /skills/mechanics/runaitargetselector
  [Send Action Message]: /skills/mechanics/sendactionmessage
  [Send Resource Pack]: /skills/mechanics/sendresourcepack
  [Send Title Message]: /skills/mechanics/sendtitlemessage
  [Send Toast]: /skills/mechanics/sendtoast
  [Set AI]: /skills/mechanics/setai
  [Set Block Type]: /skills/mechanics/setblocktype
  [Set Game Mode]: /skills/mechanics/setgamemode
  [Set Gliding]: /skills/mechanics/setgliding
  [Set Global Score]: /skills/mechanics/setglobalscore
  [Set Gravity]: /skills/mechanics/setgravity
  [Set Health]: /skills/mechanics/sethealth
  [Set Level]: /skills/mechanics/setlevel
  [Set Max Health]: /skills/mechanics/setmaxhealth
  [Set Mob Color]: /skills/mechanics/setmobcolor
  [Set Mob Score]: /skills/mechanics/setmobscore
  [Set Name]: /skills/mechanics/setname
  [Set NoDamageTicks]: /skills/mechanics/setnodamageticks
  [Set Owner]: /skills/mechanics/setowner
  [Set Rotation]: /skills/mechanics/setrotation
  [Set Target Score]: /skills/mechanics/settargetscore
  [Set Score]: /skills/mechanics/setscore
  [Set Speed]: /skills/mechanics/setspeed
  [Set Stance]: /skills/mechanics/setstance
  [Shield]: /skills/mechanics/shield
  [Shield Percent]: /skills/mechanics/shieldpercent
  [Shoot Fireball]: /skills/mechanics/shootfireball
  [Shoot Potion]: /skills/mechanics/shootpotion
  [Shoot Skull]: /skills/mechanics/shootskull
  [Shoot Shulker Bullet]: /skills/mechanics/shootshulkerbullet
  [Signal]: /skills/mechanics/signal
  [Speak]: /skills/mechanics/speak
  [Spring]: /skills/mechanics/spring
  [Stun]: /skills/mechanics/stun
  [Suicide]: /skills/mechanics/suicide
  [Summon]: /skills/mechanics/summon
  [Add Tag]: /skills/mechanics/addtag
  [Remove Tag]: /skills/mechanics/removetag
  [Take Item]: /skills/mechanics/takeitem
  [Teleport]: /skills/mechanics/teleport
  [Teleport In]: /skills/mechanics/teleportin
  [Teleport To]: /skills/mechanics/teleportto
  [Threat]: /skills/mechanics/threat
  [Throw]: /skills/mechanics/throw
  [Toggle Lever]: /skills/mechanics/togglelever
  [Toggle Sitting]: /skills/mechanics/togglesitting
  [Velocity]: /skills/mechanics/velocity
  [Weather]: /skills/mechanics/weather
  [Wolf Sit]: /skills/mechanics/wolfsit
  [View the list of Effect Mechanics by clicking here]: /skills/effects/
  [Skill]: /skills/mechanics/skill
  [Aura]: /skills/mechanics/aura
  [Cancel Event]: /skills/mechanics/cancelevent
  [Cast]: /skills/mechanics/cast
  [Chain]: /skills/mechanics/chain
  [Chain Missile]: /skills/mechanics/chainmissile
  [Delay]: /skills/mechanics/delay
  [Global Cooldown]: /skills/mechanics/globalcooldown
  [Missile]: /skills/mechanics/missile
  [Modify Projectile]: /skills/mechanics/modifyprojectile
  [On Attack]: /skills/mechanics/onattack
  [On Damaged]: /skills/mechanics/ondamaged
  [On Jump]: /skills/mechanics/onjump
  [On Shoot]: /skills/mechanics/onshoot
  [On Swing]: /skills/mechanics/onswing
  [On Use]: /skills/mechanics/onuse
  [Orbital]: /skills/mechanics/orbital
  [Projectile]: /skills/mechanics/projectile
  [PlayBlockBreakSound]: skills/mechanics/PlayBlockBreakSound
  [PlayBlockFallSound]: skills/mechanics/PlayBlockFallSound
  [PlayBlockHitSound]: skills/mechanics/PlayBlockHitSound
  [PlayBlockPlaceSound]: skills/mechanics/PlayBlockPlaceSound
  [PlayBlockStepSound]: skills/mechanics/PlayBlockStepSound
  [Shoot]: /skills/mechanics/shoot
  [Volley]: /skills/mechanics/volley
  [Sudo Skill]: /skills/mechanics/sudoskill
  [Random Skill]: /skills/mechanics/randomskill
  [Totem]: /skills/mechanics/totem
  [Variable Add]: /skills/mechanics/variableadd
  [Variable Math]: /skills/mechanics/variablemath
  [Set Variable]: /skills/mechanics/setvariable
  [Variable Unset]: /skills/mechanics/variableunset
  [Variable Subtract]: /skills/mechanics/variablesubtract
  [Swap]: /skills/mechanics/swap
  [Time]: /skills/mechanics/time
  [Hide From Players]: /skills/mechanics/hidefromplayers
  [Track Location]: /skills/mechanics/tracklocation
  [Disguise As Block]: /skills/mechanics/disguiseasblock
  [Give Item From Slot]: /skills/mechanics/giveitemfromslot
  [On Block Break]: /skills/mechanics/onblockbreak
  [On Block Place]: /skills/mechanics/onblockplace
  [On Swing]: /skills/mechanics/onswing
  [On Interact]: /skills/mechanics/oninteract
  [On Jump]: /skills/mechanics/onjump
  [On Death]: /skills/mechanics/ondeath
  [Shield Break]: /skills/mechanics/shieldbreak
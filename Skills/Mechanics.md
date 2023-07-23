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

| Mechanic                  | Description                                                                              |
|---------------------------|------------------------------------------------------------------------------------------|
| [ActivateSpawner][]       | Activates a MythicMobs spawner at the targeted location                                  |
| [AddTrade][]              | Changes the trades of a villager                                                          |
| [AnimateArmorStand][]     | Animates an armorstand                                                                   |
| [ArrowVolley][]           | Fires a volley of arrows                                                                 |
| [Attribute][]             | Sets an attribute on the target entity, if attributable                                                                 |
| [AttributeModifier][]     | Adds an attribute modifier to the attributable target                                                                 |
| [AuraRemove][]            | Removes an aura from the target entity                                                   |
| [BarCreate][]             | Creates a custom boss bar on the casting mob                                             |
| [BarRemove][]             | Removes a custom boss bar on the casting mob                                             |
| [BarSet][]                | Modifies a custom boss bar on the casting mob                                            |
| [BlockDestabilize][]      | Causes the targeted blocks to fall, as if affected by gravity                                                          |
| [BlockPhysics][]          | Triggers a block physics update at the target location                                          |
| [BoneMeal][]              | Applies a bone meal effect to the target blocks                                          |
| [BossBorder][]            | Creates an inescapable border around the mob                                |
| [BreakBlock][]            | Breaks the block at the target location                                                  |
| [BreakBlockAndGiveItem][] | Breaks the block at the target location and gives an item/droptable                      |
| [ClearExperienceLevels][] | Clears the experience levels for the targeted players                                                     |
| [GiveExperienceLevels][]  | Gives experience levels to the targeted players                                                     |
| [TakeExperienceLevels][]  | Takes experience levels to the targeted players                                                     |
| [CloseInventory][]        | Closes the target player's inventory                                                     |
| [Command][]               | Executes a command for each target                                                       |
| [Consume][]               | Deals damage and restores health per target hit                                          |
| [ConsumeSlot][]           | Remove an item from a specific slot of the player's inventory                            |
| [Disengage][]             | Causes the caster to leap backwards away from the target entity                          |
| [Disguise][]              | Changes the caster's disguise                                                            |
| [DisguiseModify][]        | Modifies the caster's already applied disguise                                                            |
| [DisguiseTarget][]        | Changes the target's disguise                                                            |
| [Undisguise][]            | Remove the caster's disguise                                                             |
| [Dismount][]              | Makes the caster dismount whatever they're riding                                        |
| [DisplayTransformation][] | Sets the targeted display entity's transformations                                        |
| [ClearThreat][]           | Makes a mob clear its threat table                                                       |
| [CurrencyGive][]          | Give money to a player. Requires Vault and a currency plugin                             |
| [CurrencyTake][]          | Take money from a player. Requires Vault and a currency plugin                           |
| [Damage][]                | Damages the target for an amount                                                         |
| [BaseDamage][]            | Damages the target for a percent of the mob's damage stat                                |
| [DamagePercent][]         | Damages the target for a percent of their health                                         |
| [DisguiseAsBlock][]       |                                                                                          |
| [Decapitate][]            | Drops a player head item based on target                                                 |
| [Doppleganger][]          | Copies the appearance of the target player                                               |
| [DropItem][]              | Drops an item or droptable at the target location                                        |
| [EjectPassenger][]        | Ejects anything riding the caster                                                        |
| [Equip][]                 | Causes the casting mob to equip an item                                                  |
| [Explosion][]             | Causes an explosion                                                                      |
| [Extinguish][]            | Removes fire ticks from the target entity                                                |
| [FawePaste][]             | Pastes a Schematic using FAWE (Fast Async World Edit)                                    |
| [Feed][]                  | Feeds the target player                                                                  |
| [FillChest][]             | Fills a chest with items, or a droptable                                                 |
| [Fly][]                   | Applies an [aura][] that allows the targeted player to fly                               |
| [ForcePull][]             | Teleports the target to the caster                                                       |
| [Freeze][]                | Freezes the target for the given number of ticks using the Powdered Snow freezing effect |
| [Glow][]                  | Makes the target glow                                                                    |
| [GiveItem][]              | Gives an item to the target                                                              |
| [GiveItemFromSlot][]      | Gives an item to the target from the item in the given slot of caster                    |
| [GoTo][]                  | Move toward the location of the targeter (entity or location)                            |
| [Heal][]                  | Heals the target                                                                         |
| [HealPercent][]           | Heals the target for a percentage of its max-health                                      |
| [Hide][]                  | Hides the caster from the targeted player(s) for a set duration.                         |
| [Hologram][]              | Summons a hologram to the targeted location                                              |
| [Ignite][]                | Sets the target on fire                                                                  |
| [JSONMessage][]           | Sends a JSON-format message to the target player(s)                                      |
| [Jump][]                  | Causes the caster to jump                                                                |
| [Leap][]                  | Causes the caster to leap towards the target                                             |
| [Lightning][]             | Strikes lightning at the target                                                          |
| [Look][]                  | Causes the caster to look at the target                                                  |
| [Lunge][]                 | Causes the caster to lunge forward at the target                                         |
| [Message][]               | Sends a message to the target player(s)                                                  |
| [ModifyGlobalScore][]     | Modifies a scoreboard value of the fake player: \_\_GLOBAL\_\_                           |
| [ModifyTargetScore][]     | Modifies a scoreboard value of the target                                                |
| [ModifyMobScore][]     | Modifies a scoreboard value of the casting mob                                                |
| [ModifyScore][]           | Modifies the score of a dummy player                                                     |
| [Mount][]                 | Summons a mob for the caster and mounts it                                               |
| [MountMe][]               | Forces the targeted entity to mount the caster                                           |
| [MountTarget][]           | Mounts the target                                                                        |
| [Oxygen][]                | Gives oxygen to a player target                                                          |
| [PickUpItem][]            | Pick up the targeted item                                                                |
| [PlayBlockBreakSound][]   | Plays a block breaking sound                                                             |
| [PlayBlockFallSound][]    | Plays a block falling sound                                                              |
| [PlayBlockHitSound][]     | Plays a block hit sound                                                                  |
| [PlayBlockPlaceSound][]   | Plays a block place sound                                                                |
| [PlayBlockStepSound][]    | Plays a block step sound                                                                 |
| [PoseArmorStand][]        | Changes the pose of the target ArmorStand                                                |
| [Potion][]                | Applies a potion effect to the target                                                    |
| [PotionClear][]           | Removes all potion effects from target entity                                            |
| [Prison][]                | Imprisons the target inside a block                                                      |
| [Propel][]                | Propels the caster towards the target                                                      |
| [Pull][]                  | Pulls the target towards the mob                                                         |
| [PushButton][]            | Pushes a button at the target location                                                   |
| [RayTrace][]              | Traces a straight line to the target                                                     |
| [RayTraceTo][]            | Executes a skill with the result of a raytrace to the target location                    |
| [Rally][]                 | Causes other nearby mobs to attack the target                                            |
| [RandomMessage][]         | Sends a random message to the target player                                              |
| [Remount][]               | Remounts the mob the caster originally spawned riding, if it is still alive              |
| [Remove][]                | Removes the target mob                                                                   |
| [RemoveHeldItem][]        | Removes some of the item the target player is holding                                    |
| [RemoveOwner][]           | Removes the ownership of the target mob                                                  |
| [RunAIGoalSelector][]     | Change the target's AIGoalSelectors                                                      |
| [RunAITargetSelector][]   | Change the target's AITargetSelectors                                                    |
| [Saddle][]                | Equips or remove a saddle on the target entity                                          |
| [SendActionMessage][]     | Sends an Actionbar Message to the target player                                          |
| [SendResourcePack][]      | Sends a Resource Pack to the target player                                               |
| [SendTitleMessage][]      | Sends a Title/Subtitle Message to the target player                                      |
| [SendToast][]             | Sends an achievement toast to the target player                                          |
| [SetAI][]                 | Disables/enables the AI of the target mob                                                |
| [SetBlockType][]          | Change block type at target location                                                     |
| [SetCollidable][]         | Sets if the target should have a collidable hitbox or not                                                     |
| [SetDragonPodium][]       | Sets the position of the dragon's podium at the target location                                                     |
| [SetGameMode][]           | Sets the Game Mode of the target player                                                  |
| [SetGliding][]            | Makes the target glide if they have elytra                                               |
| [SetGlobalScore][]        | Sets a scoreboard value on the fake player: \_\_GLOBAL\_\_                               |
| [SetGravity][]            | Sets whether gravity affects the target entity                                           |
| [SetHealth][]             | Sets the health of the target entity                                                     |
| [SetLeashHolder][]              | Changes the holder of a mobs lead                                                          |
| [SetLevel][]              | Changes the casting mob's level                                                          |
| [SetMaterialCooldown][]              | sets a cooldown for usable materials like ender pearls, chorus fruit, etc                                                          |
| [SetMaxHealth][]          | Sets the max health of the target entity                                                 |
| [SetMobColor][]           | Changes the color of the target if it is a colorable mob                                 |
| [SetMobScore][]           | Sets a scoreboard value on the casting mob                                               |
| [SetName][]               | Changes the target entity's name                                                         |
| [SetRaiderPatrolBlock][]  | Sets the target raider to patrol a location                                                         |
| [SetRaiderPatrolLeader][] | Sets the raider patrol leader                                                         |
| [SetFaction][]            | Changes the target entity's faction                                                      |
| [SetNoDamageTicks][]      | Sets the nodamageticks of the target                                                     |
| [SetOwner][]              | Makes the target the owner of the casting mob                                            |
| [SetParent][]             | Makes the target the parent of the casting mob                                            |
| [SetProjectileDirection][]| Sets the calling projectile's movement direction to the given target                                            |
| [SetProjectileBulletModel][]    | Sets the model of the projectile. (DISPLAY bullets only)                                                                                                   |
| [SetRotation][]           | Sets the rotation of the target                                                          |
| [SetTarget][]             | Sets the caster's target                                                                 |
| [SetTargetScore][]        | Sets the score of the target                                                             |
| [SetTongueTarget][]       | Sets the tongue target for a frog caster to the target entity                            |
| [SetScore][]              | Sets the scoreboard value of a dummy player                                              |
| [SetSpeed][]              | Sets the target entity's speed attribute                                                 |
| [SetStance][]             | Sets the stance of the target mob                                                        |
| [Shield][]                | Applies an absorb shield to the target entity                                            |
| [ShieldBreak][]           | Forces the player to lower their shield and puts it on cooldown                          |
| [ShieldPercent][]         | Applies an absorb shield to the target entity for a percentage of their max health       |
| [ShootFireball][]         | Shoots a fireball at the target                                                          |
| [ShootPotion][]           | Throws a potion at the target                                                            |
| [ShootSkull][]            | Shoots a wither skull at the target                                                      |
| [ShootShulkerBullet][]    | Shoots a shulker bullet at the target entity                                             |
| [ShowEntity][]            | Shows the hidden caster to the targeted players                                          |
| [Signal][]                | Sends a signal to a mob                                                                  |
| [Speak][]                 | Causes the mob to speak in chat, with options for speech bubbles                         |
| [Spring][]                | Creates a temporary spring of liquid at the target                                       |
| [Stun][]                  | Stuns the target entity                                                                  |
| [StopUsingItem][]         | Stops the targeted entity from using an item                                             |
| [Suicide][]               | Causes the caster to die                                                                 |
| [Summon][]                | Summons other mobs at the target                                                         |
| [SummonPassenger][]                | Summons a mob to ride the target.                                                         |
| [Swap][]                  | Swaps locations with the target                                                          |
| [AddTag][]                | Adds a scoreboard tag to the target                                                      |
| [RemoveTag][]             | Removes a scoreboard tag from the target                                                 |
| [TakeItem][]              | Removes an item from the targeted player's inventory                                     |
| [Teleport][]              | Teleports to the target                                                                  |
| [TeleportY][]              | Teleports to the target vertically                                                                 |
| [TeleportIn][]            | Teleports the target relative to the caster's yaw                                        |
| [TeleportTo][]            | Teleports the target to a specified location                                             |
| [Time][]                  | Changes the time                                                                                |
| [Threat][]                | Modifies the mob's threat towards the target                                             |
| [Throw][]                 | Throws the target entity                                                                 |
| [ToggleLever][]           | Toggles a lever at the target location                                                   |
| [ToggleSitting][]         | Toggles the sitting state for cats, dogs, foxes, and parrots.               |
| [TrackLocation][]         | Sets the mob's tracked location to the targeted location                    |
| [UndoPaste][]             | Undoes a previously made paste                                              |
| [Velocity][]              | Modifies the velocity of the target entity(s)                               |
| [Weather][]               | Modifies the weather in the target world                                    |
| [WolfSit][]               | Forces a targeted wolf to sit.                                              |

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

| Mechanic                | Description                                                                                                                                             |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| **[Skill][]**           | Executes a meta-skill. The butter for your bread.                                                                                                       |
| **[VariableSkill][]**   | Executes a meta-skill. Supports placeholders.                                                                                                       |
| [Aura][]                | Applies an aura to the targeted entity, allowing for skills to be run onStart/onTick/onEnd/Etc which all originate from the target.                     |
| [CancelEvent][]         | Cancel the Event that triggered the current skill-tree. Only works for certain triggers.                                                                |
| [Cast][]                | "Casts" a meta-skill using various advanced options.                                                                                                    |
| [Chain][]               | Chains a skill between multiple targets that are near each other.                                                                                       |
| [ChainMissile][]        | A missile that chains between entities. **Premium-Only** mechanic!                                                                                      |
| [Delay][]               | Delays execution of the current skill list by a set number of ticks.                                                                                    |
| [EndProjectile][]       | Terminates the projectile. Only usable in projectile mechanics.                                                                                         |
| [GlobalCooldown][]      | Sets the caster's Global Cooldown timer                                                                                                                 |
| [Missile][]             | Fires a homing projectile towards the target.                                                                                                           |
| [ModifyProjectile][]    | Modifying the projectile / missile / orbital                                                                                                            |
| [OnAttack][]            | Applies an [aura][] to the target that triggers skills when they attack                                                                                 |
| [OnDamaged][]           | Applies an [aura][] to the target that triggers skills when they take damage                                                                            |
| [OnShoot][]             | Applies an [aura][] to the target that triggers skills when they shoot a bow                                                                            |
| [OnBlockBreak][]        | Applies an [aura][] to the target that triggers skills when they break a block                                                                          |
| [OnBlockPlace][]        | Applies an [aura][] to the target that triggers skills when they place a block                                                                          |
| [OnSwing][]             | Applies an [aura][] to the target that triggers skills when they swing / left click                                                                     |
| [OnInteract][]          | Applies an [aura][] to the target that triggers skills when they interact / right click while holding a block or looking at an outlined block (NOT AIR) |
| [OnJump][]              | Applies an [aura][] to the target that triggers a skill when they jump (PAPER ONLY MECHANIC)                                                            |
| [OnDeath][]             | Applies an [aura][] to the target that triggers a skill when they die                                                                                   |
| [Orbital][]             | Applies an [aura][] that causes a projectile to orbit around the target                                                                                 |
| [Polygon][]             | Creates a highly-customizable polygon-shaped pattern that can execute metaskills.                                                                                                                |
| [Projectile][]          | Fires a highly-customizable projectile towards the target                                                                                               |
| [ProjectileVelocity][]  | Modifies the velocity of the calling Projectile or Missile                                                                                               |
| [RandomSkill][]         | Executes a random skill from a list                                                                                                                     |
| [SetSkillCooldown][]    | Sets the given metakill's cooldown to the given value                                                                                                   |
| [Shoot][]               | Shoots a item-projectile at the target, similar to arrows/eggs/snowballs.                                                                               |
| [Slash][]               | Creates a highly-customizable slash pattern that can execute metaskills.                                                                               |
| [SudoSkill][]           | Makes the target execute a skill                                                                                                                        |
| [Switch-Case][]         | Acts as a switch/case                                                                                                                                   |
| [Totem][]               | Creates a static "totem" at a location that can execute other skills                                                                                    |
| [Volley][]              | Shoots a volley of projectile-items at the target with various options                                                                                  |
| [VariableAdd][]         | Adds an amount to a numeric variable                                                                                                                    |
| [VariableMath][]        | Performs math on a numeric variable                                                                                                                     |
| [SetVariable][]         | Sets the value of a variable                                                                                                                            |
| [SetVariableLocation][] | Sets a variable to the target location                                                                                                                  |
| [VariableUnset][]       | Unsets the variable                                                                                                                                     |
| [VariableSubtract][]    | Subtracts an amount from a numeric variable                                                                                                             |

Universal Attributes
--------------------

The following attributes are applicable to all mechanics.

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| cooldown  | cd        | In seconds. Allows for decimal values.                               | 0       |
| delay     |           | Delays the execution of the mechanic by a set number of ticks.       | 0       |
| repeat    |           | How many times the mechanic should be repeated                       | 0       |
| repeatInterval | repeatI | How many ticks must elapse between repetitions                    | 0       |
| targetInterval | targetI | How many ticks must elapse between target selection               | 0       |
| origin **[PREMIUM]** ||Change the origin to whatever targeter is supplied. `origin=@Forward{f=10}` |   |
| forcesync | sync      | Forces the execution type to be SYNC                                 | false   |
| power     |           | [Power](/mobs/Power) multiplier                                      | 1       |
| fromorigin | fo       | Whether to cast the mechanic from origin                             | false   |
| targetisorigin |      | Whether to set the target of the mechanic to be the origin           | false   |
| targetcreative |      | Whether to target creative players                                   | false   |
| splitPower     | powersplit | Whether to split the power between targets                     | false |

<!--
Upcoming Mechanics
------------------

These mechanics are currently being worked on and will be in future
releases of the plugin. Some mechanics listed here are already included,
but not yet ready for use.

| Mechanic           | Description                     |
|--------------------|---------------------------------|
-->

  [here!]: /skills/skillparametersystem
  [Targeter]: /skills/targeters/
  [ActivateSpawner]: /skills/mechanics/activatespawner
  [AddTrade]: /skills/mechanics/AddTrade
  [AnimateArmorStand]: /skills/mechanics/animatearmorstand
  [ArrowVolley]: /skills/mechanics/arrowvolley
  [Attribute]: /skills/mechanics/Attribute
  [AttributeModifier]: /skills/mechanics/AttributeModifier
  [AuraRemove]: /skills/mechanics/auraremove
  [BarCreate]: /skills/mechanics/barcreate
  [BarSet]: /skills/mechanics/barset
  [BarRemove]: /skills/mechanics/barremove
  [BlockDestabilize]: /skills/mechanics/blockdestabilize
  [BlockPhysics]: /skills/mechanics/blockphysics
  [BoneMeal]: /skills/mechanics/bonemeal
  [BossBorder]: /skills/mechanics/bossborder
  [BreakBlock]: /skills/mechanics/breakblock
  [BreakBlockAndGiveItem]: /skills/mechanics/breakBlockAndGiveItem
  [ClearExperienceLevels]: /skills/mechanics/ClearExperienceLevels
  [GiveExperienceLevels]: /skills/mechanics/GiveExperienceLevels
  [TakeExperienceLevels]: /skills/mechanics/TakeExperienceLevels
  [CloseInventory]: /skills/mechanics/closeinventory
  [Command]: /skills/mechanics/command
  [Consume]: /skills/mechanics/consume
  [ConsumeSlot]: /skills/mechanics/consumeslot
  [Disengage]: /skills/mechanics/disengage
  [Disguise]: /skills/mechanics/disguise
  [DisguiseModify]: /skills/mechanics/DisguiseModify
  [DisguiseTarget]: /skills/mechanics/disguisetarget
  [Undisguise]: /skills/mechanics/undisguise
  [Dismount]: /skills/mechanics/dismount
  [DisplayTransformation]: /skills/mechanics/DisplayTransformation
  [ClearThreat]: /skills/mechanics/clearthreat
  [CurrencyGive]: /skills/mechanics/currencygive
  [CurrencyTake]: /skills/mechanics/currencytake
  [Damage]: /skills/mechanics/damage
  [BaseDamage]: /skills/mechanics/basedamage
  [DamagePercent]: /skills/mechanics/percentdamage
  [Decapitate]: /skills/mechanics/decapitate
  [Doppleganger]: /skills/mechanics/doppleganger
  [DropItem]: /skills/mechanics/dropitem
  [EjectPassenger]: /skills/mechanics/ejectpassenger
  [Equip]: /skills/mechanics/equip
  [Explosion]: /skills/mechanics/explosion
  [Extinguish]: /skills/mechanics/extinguish
  [FawePaste]: /skills/mechanics/fawepaste
  [Feed]: /skills/mechanics/feed
  [FillChest]: /skills/mechanics/fillChest
  [Fly]: /skills/mechanics/fly
  [Freeze]: /skills/mechanics/freeze
  [aura]: /skills/mechanics/aura
  [ForcePull]: /skills/mechanics/forcepull
  [Glow]: /skills/mechanics/glow
  [GiveItem]: /skills/mechanics/giveitem
  [GiveItemFromTarget]: /skills/mechanics/giveitemfromtarget
  [GoTo]: /skills/mechanics/goto
  [Heal]: /skills/mechanics/heal
  [HealPercent]: /skills/mechanics/healpercent
  [Hologram]: /skills/mechanics/hologram
  [Ignite]: /skills/mechanics/ignite
  [JSONMessage]: /skills/mechanics/jsonmessage
  [Jump]: /skills/mechanics/jump
  [Leap]: /skills/mechanics/leap
  [Lightning]: /skills/mechanics/lightning
  [Look]: /skills/mechanics/look
  [Lunge]: /skills/mechanics/lunge
  [Message]: /skills/mechanics/message
  [ModifyGlobalScore]: /skills/mechanics/modifyglobalscore
  [ModifyTargetScore]: /skills/mechanics/modifytargetscore
  [ModifyMobScore]: /skills/mechanics/modifymobscore
  [ModifyScore]: /skills/mechanics/modifyscore
  [Mount]: /skills/mechanics/mount
  [MountMe]: /skills/mechanics/mountme
  [MountTarget]: /skills/mechanics/mounttarget
  [Oxygen]: /skills/mechanics/oxygen
  [PickUpItem]: /skills/mechanics/pickupitem
  [PoseArmorStand]: /skills/mechanics/posearmorstand
  [Potion]: /skills/mechanics/potion
  [PotionClear]: /skills/mechanics/potionclear
  [Prison]: /skills/mechanics/prison
  [Propel]: /skills/mechanics/propel
  [Pull]: /skills/mechanics/pull
  [PushButton]: /skills/mechanics/pushbutton
  [Rally]: /skills/mechanics/rally
  [RandomMessage]: /skills/mechanics/randommessage
  [RayTrace]: /skills/mechanics/raytrace
  [RayTraceTo]: /skills/mechanics/raytraceto
  [Remount]: /skills/mechanics/remount
  [Remove]: /skills/mechanics/remove
  [RemoveHeldItem]: /skills/mechanics/removehelditem
  [RemoveOwner]: /skills/mechanics/removeowner
  [RunAIGoalSelector]: /skills/mechanics/runaigoalselector
  [RunAITargetSelector]: /skills/mechanics/runaitargetselector
  [Saddle]: /skills/mechanics/saddle
  [SendActionMessage]: /skills/mechanics/sendactionmessage
  [SendResourcePack]: /skills/mechanics/sendresourcepack
  [SendTitleMessage]: /skills/mechanics/sendtitlemessage
  [SendToast]: /skills/mechanics/sendtoast
  [SetAI]: /skills/mechanics/setai
  [SetBlockType]: /skills/mechanics/setblocktype
  [SetCollidable]: /skills/mechanics/setcollidable
  [SetDragonPodium]: /skills/mechanics/SetDragonPodium
  [SetGameMode]: /skills/mechanics/setgamemode
  [SetGliding]: /skills/mechanics/setgliding
  [SetGlobalScore]: /skills/mechanics/setglobalscore
  [SetGravity]: /skills/mechanics/setgravity
  [SetHealth]: /skills/mechanics/sethealth
  [SetLeashHolder]: /skills/mechanics/setleashholder
  [SetLevel]: /skills/mechanics/setlevel
  [SetMaterialCooldown]: /skills/mechanics/setmaterialcooldown
  [SetMaxHealth]: /skills/mechanics/setmaxhealth
  [SetMobColor]: /skills/mechanics/setmobcolor
  [SetMobScore]: /skills/mechanics/setmobscore
  [SetName]: /skills/mechanics/setname
  [SetNoDamageTicks]: /skills/mechanics/setnodamageticks
  [SetOwner]: /skills/mechanics/setowner
  [SetParent]: /skills/mechanics/SetParent
  [SetProjectileDirection]: /skills/mechanics/SetProjectileDirection
  [SetProjectileBulletModel]: /skills/mechanics/setprojectilebulletmodel
  [SetRaiderPatrolBlock]: /skills/mechanics/setraiderpatrolblock
  [SetRaiderPatrolLeader]: /skills/mechanics/setraiderpatrolleader
  [SetRotation]: /skills/mechanics/setrotation
  [SetTarget]: /skills/mechanics/settarget
  [SetTargetScore]: /skills/mechanics/settargetscore
  [SetTongueTarget]: /skills/mechanics/settonguetarget
  [SetScore]: /skills/mechanics/setscore
  [SetSpeed]: /skills/mechanics/setspeed
  [SetStance]: /skills/mechanics/setstance
  [Shield]: /skills/mechanics/shield
  [ShieldPercent]: /skills/mechanics/shieldpercent
  [ShootFireball]: /skills/mechanics/shootfireball
  [ShootPotion]: /skills/mechanics/shootpotion
  [ShootSkull]: /skills/mechanics/shootskull
  [ShootShulkerBullet]: /skills/mechanics/shootshulkerbullet
  [ShowEntity]: /skills/mechanics/showentity
  [Signal]: /skills/mechanics/signal
  [Speak]: /skills/mechanics/speak
  [Spring]: /skills/mechanics/spring
  [StopUsingItem]: /skills/mechanics/stopusingitem
  [Stun]: /skills/mechanics/stun
  [Suicide]: /skills/mechanics/suicide
  [Summon]: /skills/mechanics/summon
  [SummonPassenger]: /skills/mechanics/summonpassenger
  [AddTag]: /skills/mechanics/addtag
  [RemoveTag]: /skills/mechanics/removetag
  [TakeItem]: /skills/mechanics/takeitem
  [Teleport]: /skills/mechanics/teleport
  [TeleportY]: /skills/mechanics/teleporty
  [TeleportIn]: /skills/mechanics/teleportin
  [TeleportTo]: /skills/mechanics/teleportto
  [Threat]: /skills/mechanics/threat
  [Throw]: /skills/mechanics/throw
  [ToggleLever]: /skills/mechanics/togglelever
  [ToggleSitting]: /skills/mechanics/togglesitting
  [UndoPaste]: /skills/mechanics/undopaste
  [Velocity]: /skills/mechanics/velocity
  [Weather]: /skills/mechanics/weather
  [WolfSit]: /skills/mechanics/wolfsit
  [View the list of Effect Mechanics by clicking here]: /skills/effects/
  
  
  <!-- METAMECHANICS -->
  [Skill]: /skills/mechanics/skill
  [VariableSkill]: /skills/mechanics/variableskill
  [Aura]: /skills/mechanics/aura
  [CancelEvent]: /skills/mechanics/cancelevent
  [Cast]: /skills/mechanics/cast
  [Chain]: /skills/mechanics/chain
  [ChainMissile]: /skills/mechanics/chainmissile
  [Delay]: /skills/mechanics/delay
  [EndProjectile]: /skills/mechanics/endprojectile
  [GlobalCooldown]: /skills/mechanics/globalcooldown
  [Missile]: /skills/mechanics/missile
  [ModifyProjectile]: /skills/mechanics/modifyprojectile
  [OnAttack]: /skills/mechanics/onattack
  [OnDamaged]: /skills/mechanics/ondamaged
  [OnJump]: /skills/mechanics/onjump
  [OnShoot]: /skills/mechanics/onshoot
  [OnSwing]: /skills/mechanics/onswing
  [OnUse]: /skills/mechanics/onuse
  [Orbital]: /skills/mechanics/orbital
  [Polygon]: /skills/mechanics/polygon
  [Projectile]: /skills/mechanics/projectile
  [ProjectileVelocity]: /skills/mechanics/projectilevelocity
  [PlayBlockBreakSound]: skills/mechanics/PlayBlockBreakSound
  [PlayBlockFallSound]: skills/mechanics/PlayBlockFallSound
  [PlayBlockHitSound]: skills/mechanics/PlayBlockHitSound
  [PlayBlockPlaceSound]: skills/mechanics/PlayBlockPlaceSound
  [PlayBlockStepSound]: skills/mechanics/PlayBlockStepSound
  [Shoot]: /skills/mechanics/shoot
  [Slash]: /skills/mechanics/slash
  [Volley]: /skills/mechanics/volley
  [SudoSkill]: /skills/mechanics/sudoskill
  [RandomSkill]: /skills/mechanics/randomskill
  [SetSkillCooldown]: /skills/mechanics/setskillcooldown
  [Totem]: /skills/mechanics/totem
  [VariableAdd]: /skills/mechanics/variableadd
  [VariableMath]: /skills/mechanics/variablemath
  [SetVariable]: /skills/mechanics/setvariable
  [SetVariableLocation]: /skills/mechanics/setvariablelocation
  [VariableUnset]: /skills/mechanics/variableunset
  [VariableSubtract]: /skills/mechanics/variablesubtract
  [Swap]: /skills/mechanics/swap
  [Time]: /skills/mechanics/time
  [Hide]: /skills/mechanics/hide
  [TrackLocation]: /skills/mechanics/tracklocation
  [DisguiseAsBlock]: /skills/mechanics/disguiseasblock
  [GiveItemFromSlot]: /skills/mechanics/giveitemfromslot
  [OnBlockBreak]: /skills/mechanics/onblockbreak
  [OnBlockPlace]: /skills/mechanics/onblockplace
  [OnSwing]: /skills/mechanics/onswing
  [OnInteract]: /skills/mechanics/oninteract
  [OnJump]: /skills/mechanics/onjump
  [OnDeath]: /skills/mechanics/ondeath
  [ShieldBreak]: /skills/mechanics/shieldbreak
  [Switch-Case]: /skills/mechanics/switch-case
  [SetFaction]: /skills/mechanics/setFaction
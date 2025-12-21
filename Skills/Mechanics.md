Skill Mechanics (or base skills) are simple skills that are built into
MythicMobs. You can call these basic skills by themselves in your mob's
Skill List, or you can create your own meta-skill by combining these
mechanics together.

Some Mechanics are able to target Entities, Locations, or both! Some
don't target anything. You control what your skill targets using a
[Targeter][].  

You can also find some of the mechanics listed by tag [here](/Skills/Tags/Mechanic-Tags)


[[_TOC_]]


# Additional Mechanics
Links to mechanics added by addon plugins. Any mechanics from these links will not work without that plugin installed.

- [ModelEngine 4](/../../../model-engine-4/-/wikis/Skills/Mechanics)
- [Mythic Crucible](/../../../mythiccrucible/-/wikis/Skills/Mechanics)
- [Mythic Enchantments](/../../../mythicenchants/-/wikis/Skills/Mechanics)
- [MCPets](https://mcpets.gitbook.io/mcpets/tutorials/mythicmobs-features#mechanics)


# Mechanics
These skills usually target entities (players or other mobs), but some
are able to target locations as well.
| Mechanic                  | Description                                                                              |
|---------------------------|------------------------------------------------------------------------------------------|
| [ActivateSpawner][]       | Activates a MythicMobs spawner at the targeted location                                  |
| [AddTrade][]              | Changes the trades of a villager                                                          |
| [AnimateArmorStand][]     | Animates an armorstand                                                                   |
| [ArmAnimation][]          | Makes the caster swing their arm                                                                   |
| [ArrowVolley][]           | Fires a volley of arrows                                                                 |
| [Attribute][]             | Sets an attribute on the target entity, if attributable                                                                 |
| [AttributeModifier][]     | Adds an attribute modifier to the attributable target                                                                 |
| [AuraRemove][]            | Removes an [aura] from the target entity                                                   |
| [BarCreate][]             | Creates a custom boss bar on the casting mob                                             |
| [BarRemove][]             | Removes a custom boss bar on the casting mob                                             |
| [BarSet][]                | Modifies a custom boss bar on the casting mob                                            |
| [BlackScreen][]           | Blacks out the target's screen for the duration                             |
| [BlockDestabilize][]      | Causes the targeted blocks to fall, as if affected by gravity                                                          |
| [BlockMask][]             | Temporarily masks a block as a different block                              |
| [BlockUnmask][]           | Unmasks blocks that have been masked                                        |
| [BlockPhysics][]          | Triggers a block physics update at the target location                                          |
| [BlockWave][]             | Creates a wave of blocks at the target location                             |
| [BloodyScreen][]          | Makes the target's screen glow red                                          |
| [BoneMeal][]              | Applies a bone meal effect to the target blocks                                          |
| [BossBorder][]            | Creates an inescapable border around the mob                                |
| [Bouncy][]                | Applies an [aura] to the target that makes it bouncy                                |
| [BreakBlock][]            | Breaks the block at the target location                                                  |
| [BreakBlockAndGiveItem][] | Breaks the block at the target location and gives an item/droptable                      |
| [ClearExperience][]       | Clears the experience for the targeted players                                                     |
| [ClearExperienceLevels][] | Clears the experience levels for the targeted players                                                     |
| [ClearTarget][]           | Forces the target of the mechanic to reset its current target                                                     |
| [GiveExperienceLevels][]  | Gives experience levels to the targeted players                                                     |
| [TakeExperienceLevels][]  | Takes experience levels to the targeted players                                                     |
| [CloseInventory][]        | Closes the target player's inventory                                                     |
| [Command][]               | Executes a command for each target                                                       |
| [Consume][]               | Deals damage and restores health per target hit                                          |
| [ConsumeSlot][]           | Remove an item from a specific slot of the player's inventory                            |
| [DirectionalVelocity]     | Changes the velocity on the target entity on a specific vector              |
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
| [PercentDamage][]         | Damages the target for a percent of their health                                         |
| [Decapitate][]            | Drops a player head item based on target                                                 |
| [Doppleganger][]          | Copies the appearance of the target player                                               |
| [DropItem][]              | Drops an item or droptable at the target location                                        |
| [EjectPassenger][]        | Ejects anything riding the caster                                                        |
| [Ender][]                 | Causes the "Ender" effect                                                   |
| [EnderBeam][]             | Creates a EnderCrystal's beam effect to the target                          |
| [EnderDragonResetCrystals][] | Generates the EnderDragon crystals                                                   |
| [EnderDragonSetPhase][]   | Sets the EnderDragon phase                                                   |
| [EnderDragonSetRespawnPhase][] | Sets the EnderDragon respawn phase                                                   |
| [EnderDragonSpawnPortal][] | Generates the portal of the EnderDragon battle                                                   |
| [Equip][]                 | Causes the casting mob to equip an item                                                  |
| [EquipCopy][]             | Causes the caster to equip a copy of the target's equipment                                                  |
| [Explosion][]             | Causes an explosion                                                                      |
| [FakeExplosion][]         | Causes a fake explosion                                                                      |
| [Extinguish][]            | Removes fire ticks from the target entity                                                |
| [FawePaste][]             | Pastes a Schematic using FAWE (Fast Async World Edit)                                    |
| [Feed][]                  | Feeds the target player                                                                  |
| [Fear][]                  | Applies an aura that makes the target run around in fear                                                                  |
| [FillChest][]             | Fills a chest with items, or a droptable                                                 |
| [Firework][]              | Creates a firework effect at the target                                             |
| [Flames][]                | Creates the flames effect at the location of the targeter                               |
| [Fly][]                   | Applies an [aura][] that allows the targeted player to fly                               |
| [ForcePull][]             | Teleports the target to the caster                                                       |
| [Freeze][]                | Freezes the target for the given number of ticks using the Powdered Snow freezing effect |
| [Geyser][]                | Creates a "geyser" of water or lava                                                                   |
| [GiveItem][]              | Gives an item to the target                                                              |
| [GiveItemFromSlot][]      | Gives an item to the target from the item in the given slot of caster                    |
| [GiveItemFromTarget][]    | Gives the caster an item while playing the pickup-item animation from the target entity or location   |
| [Glow][]                  | Makes the target glow                                                                    |
| [GoatRam][]               | Causes the casting goat mob to ram the targeted entity                            |
| [GoTo][]                  | Move toward the location of the targeter (entity or location)                            |
| [GuardianBeam][]          | Draws a guardian beam between the origin and the target                                                                  |
| [Heal][]                  | Heals the target                                                                         |
| [HealPercent][]           | Heals the target for a percentage of its max-health                                      |
| [Hide][]                  | Hides the caster from the targeted player(s) for a set duration.                         |
| [Hit][]                   | Simulates a physical hit from the mob.                                                  |
| [Hologram][]              | Summons a hologram to the targeted location                                              |
| [Ignite][]                | Sets the target on fire                                                                  |
| [ItemSpray][]             | Causes an explosion of temporary items at the target location                                                             |
| [JSONMessage][]           | Sends a JSON-format message to the target player(s)                                      |
| [Jump][]                  | Causes the caster to jump                                                                |
| [Leap][]                  | Causes the caster to leap towards the target                                             |
| [Lightning][]             | Strikes lightning at the target                                                          |
| [FakeLightning][]         | Strikes a fake lightning at the target                                                          |
| [Log][]                   | Logs a message to console.                                                  |
| [Look][]                  | Causes the caster to look at the target                                                  |
| [Lunge][]                 | Causes the caster to lunge forward at the target                                         |
| [MatchRotation][]         | Sets the caster's yaw and pitch to the same value of the target's           |
| [Message][]               | Sends a message to the target player(s)                                                  |
| [ModifyDamage][]          | Modifies the damage event that triggered the skill                                                         |
| [ModifyGlobalScore][]     | Modifies a scoreboard value of the fake player: \_\_GLOBAL\_\_                           |
| [ModifyTargetScore][]     | Modifies a scoreboard value of the target                                                |
| [ModifyMobScore][]        | Modifies a scoreboard value of the casting mob                                                |
| [ModifyScore][]           | Modifies the score of a dummy player                                                     |
| [Mount][]                 | Summons a mob for the caster and mounts it                                               |
| [MountMe][]               | Forces the targeted entity to mount the caster                                           |
| [MountTarget][]           | Mounts the target                                                                        |
| [MovePin][]               | Moves the given pin to the target location                                      |
| [OpenCustomMenu]          | Opens a [custom menu]                                                      |
| [OpenTrades][]            | Opens the trades of the casting villager to the target player               |
| [Oxygen][]                | Gives oxygen to a player target                                                          |
| [Particle][]              | Creates particle effects around the target                                                                |
| [ParticleBox][]           | Draws a box of particles around the target                                                                |
| [ParticleEquation][]      | Generates particles based on equations                                                                |
| [ParticleLine][]          | Draws a line of particle effects to the target                                                                |
| [ParticleLineHelix][]     | Draws a line based helix effect                                                                |
| [ParticleLineRing][]      | Draws a particle ring connected by lines                                                                |
| [ParticleOrbital][]       | Draws orbiting particle effects around the target                                                                |
| [ParticleRing][]          | Draws a ring of particles around the target                                                                |
| [ParticleSphere][]        | Draws a sphere of particles around the target                                                               |
| [ParticleTornado][]       | Draws a persistent "tornado" of particles at the target                     |
| [Atom][]                  | Creates some particles in the shape of an atom                              |
| [PickUpItem][]            | Pick up the targeted item                                                                |
| [PlayAnimation][]         | Forces the entity to play an animation                                      |
| [PlayBlockBreakSound][]   | Plays a block breaking sound                                                             |
| [PlayBlockFallSound][]    | Plays a block falling sound                                                              |
| [PlayBlockHitSound][]     | Plays a block hit sound                                                                  |
| [PlayBlockPlaceSound][]   | Plays a block place sound                                                                |
| [PlayBlockStepSound][]    | Plays a block step sound                                                                 |
| [PoseArmorStand][]        | Changes the pose of the target ArmorStand                                                |
| [Potion][]                | Applies a potion effect to the target                                                    |
| [PotionClear][]           | Removes all potion effects from target entity                                            |
| [Prison][]                | Imprisons the target inside a block                                                      |
| [PrintParentTree]         | Prints debug information regarding the Metaskill executing the mechanic and its SkillTree |
| [Propel][]                | Propels the caster towards the target                                                      |
| [Pull][]                  | Pulls the target towards the mob                                                         |
| [PushBlock][]             | Pushes the block at the target location in the given direction                                                          |
| [PushButton][]            | Pushes a button at the target location                                                   |
| [RayTrace][]              | Traces a straight line to the target                                                     |
| [RayTraceTo][]            | Executes a skill with the result of a raytrace to the target location                    |
| [Rally][]                 | Causes other nearby mobs to attack the target                                            |
| [RandomMessage][]         | Sends a random message to the target player                                              |
| [Recoil][]                | Kicks the target's screen in order to simulate a recoil                     |
| [Remount][]               | Remounts the mob the caster originally spawned riding, if it is still alive              |
| [Remove][]                | Removes the target mob                                                                   |
| [RemoveHeldItem][]        | Removes some of the item the target player is holding                                    |
| [RemoveOwner][]           | Removes the ownership of the target mob                                                  |
| [ResetAI][]               | Attempts to resets the AI of a casting mob to the base type's default                                                  |
| [RotateTowards][]         | Rotates the caster towards the target location                                   |
| [RunAIGoalSelector][]     | Change the caster's [AIGoalSelectors]                                                      |
| [RunAITargetSelector][]   | Change the caster's [AITargetSelectors]                                                    |
| [Saddle][]                | Equips or remove a saddle on the target entity                                          |
| [SendActionMessage][]     | Sends an Actionbar Message to the target player                                          |
| [SendResourcePack][]      | Sends a Resource Pack to the target player                                               |
| [SendTitle][]             | Sends a Title/Subtitle Message to the target player                                      |
| [SendToast][]             | Sends an achievement toast to the target player                                          |
| [SetAI][]                 | Disables/enables the AI of the target mob                                                |
| [SetBlockOpen][]          | Sets the target block's open state                                                |
| [SetBlockType][]          | Change block type at target location                                                     |
| [SetChunkForceLoaded][]   | Sets the force-loaded status of a location's chunk                                                     |
| [SetCollidable][]         | Sets if the target should have a collidable hitbox or not                                                     |
| [SetCustomMenuButton][]   | Sets a specific slot of the opened [custom menu] to the specified button |
| [SetDragonPodium][]       | Sets the position of the dragon's podium at the target location                                                     |
| [SetGameMode][]           | Sets the Game Mode of the target player                                                  |
| [SetGliding][]            | Makes the target glide if they have elytra                                               |
| [SetGlobalScore][]        | Sets a scoreboard value on the fake player: \_\_GLOBAL\_\_                               |
| [SetGravity][]            | Sets whether gravity affects the target entity                                           |
| [SetHealth][]             | Sets the health of the target entity                                                     |
| [SetInteractionSize][]    | Sets the size of the target `INTERACTION` entity.                                                     |
| [SetItemGroupCooldown][]  | Sets the cooldown on an item group for the target player                                                     |
| [setDisplayEntityItem][]  | Sets the item component of `ITEM_DISPLAY` entities.                                                     |
| [SetLeashHolder][]        | Changes the holder of a mobs lead                                                          |
| [SetLevel][]              | Changes the casting mob's level                                                          |
| [SetMaterialCooldown][]   | Sets a cooldown for usable materials like ender pearls, chorus fruit, etc                                                          |
| [SetMaxHealth][]          | Sets the max health of the target entity                                                 |
| [SetMobColor][]           | Changes the color of the target if it is a colorable mob                                 |
| [SetMobScore][]           | Sets a scoreboard value on the casting mob                                               |
| [SetName][]               | Changes the caster entity's name                                                         |
| [setRaiderCanJoinRaid][]  | Sets if the target raider entity can join a raid or not                                                         |
| [SetRaiderPatrolBlock][]  | Sets the target raider to patrol a location                                                         |
| [SetRaiderPatrolLeader][] | Sets the raider patrol leader                                                         |
| [SetFaction][]            | Changes the target entity's faction                                                      |
| [SetFlying][]             | Sets whether the target player is flying                                                      |
| [SetNoDamageTicks][]      | Sets the nodamageticks of the target                                                     |
| [SetOwner][]              | Makes the target the owner of the casting mob                                            |
| [SetParent][]             | Makes the target the parent of the casting mob                                            |
| [SetPathfindingMalus][]   | Sets the pathfinding malus of a mob for given terrain types                                            |
| [SetPitch][]              | Sets the head pitch of the target entity                                            |
| [SetPose][]               | Sets the entity's pose                                                          |
| [SetRotation][]           | Sets the rotation of the target                                                          |
| [SetTarget][]             | Sets the caster's target                                                                 |
| [SetTargetScore][]        | Sets the score of the target                                                             |
| [SetTextDisplay][]        | Sets the text component of target Text Display entity                       |
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
| [Skybox][]                | Alters the target player's skybox                                           |
| [Smoke][]                 | Creates a puff of smoke                                                     |
| [SmokeSwirl][]            | Creates a persistent "swirl" of smoke                                       |
| [Sound][]                 | Plays a sound effect from both vanilla Minecraft and resource packs         |
| [StealItem][]             | Steals an item from the target and puts it in the mob's hand                                           |
| [StopSound][]             | Stops a sound effect from playing                                           |
| [Speak][]                 | Causes the mob to speak in chat, with options for speech bubbles                         |
| [Spin][]                  | Causes the target to spin                                                   |
| [Spring][]                | Creates a temporary spring of liquid at the target                                       |
| [Stun][]                  | Applies an [aura] that stuns the target entity                                                                  |
| [StopUsingItem][]         | Stops the targeted entity from using an item                                             |
| [Suicide][]               | Causes the caster to die                                                                 |
| [Summon][]                | Summons other mobs at the target                                                         |
| [SummonAreaEffectCloud][] | Summons a cloud of particles at the target                                     |
| [SummonFallingBlock][]    | Summons a falling block                                                                          |
| [SummonPassenger][]       | Summons a mob to ride the target.                                                         |
| [Swap][]                  | Swaps locations with the target                                                          |
| [SwingOffhand][]          | Makes the casting player swing their offhand                                                          |
| [AddTag][]                | Adds a scoreboard tag to the target                                                      |
| [RemoveTag][]             | Removes a scoreboard tag from the target                                                 |
| [TakeItem][]              | Removes an item from the targeted player's inventory                                     |
| [Taunt][]                 | Modifies the threat level that the caster holds with the target entities                                     |
| [Teleport][]              | Teleports to the target                                                                  |
| [TeleportY][]             | Teleports the caster vertically                                                                 |
| [TeleportIn][]            | Teleports the target relative to the caster's yaw                                        |
| [TeleportTo][]            | Teleports the target to a specified location                                             |
| [Time][]                  | Changes the time                                                                                |
| [Threat][]                | Modifies the mob's threat towards the target                                             |
| [Throw][]                 | Throws the target entity                                                                 |
| [ThunderLevel][]          | Creates a client-side, per-player rainless storm                            |
| [ToggleLever][]           | Toggles a lever at the target location                                                   |
| [TogglePiston][]          | Toggles a piston at the target location                                     |
| [ToggleSitting][]         | Toggles the sitting state for cats, dogs, foxes, and parrots.               |
| [TotemOfUndying][]        | Plays the effect of a player resurrecting                                   |
| [TrackLocation][]         | Sets the mob's tracked location to the targeted location                    |
| [UndoPaste][]             | Undoes a previously made paste                                              |
| [Velocity][]              | Modifies the velocity of the target entity(s)                               |
| [Weather][]               | Modifies the weather in the target world                                    |
| [WolfSit][]               | Forces a targeted wolf to sit.                                              |
| [WorldEditReplace][]      | Replaces blocks in a region using WorldEdit                                              |


## Meta Mechanics

These skill mechanics have special advanced functions, and most are used
to call other skills. If you specify a target, all other skills called
by these will "inherit" the targets (if applicable).

| Mechanic                | Description                                                                                                                                             |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| **[Skill][]**           | Executes a meta-skill. The butter for your bread.                                                                                                       |
| **[VariableSkill][]**   | Executes a meta-skill. Supports placeholders.                                                                                                       |
| [Aura][]                | Applies an aura to the targeted entity, allowing for skills to be run onStart/onTick/onEnd/Etc which all originate from the target.                     |
| [Beam][]                | Creates a beam of a material between the caster and the target  |
| [CancelEvent][]         | Cancels the Event that triggered the current skill-tree. Only works for certain triggers.                                                                |
| [CancelSkill][]         | Cancels the execution of the Metaskill when triggered.                                                                |
| [Cast][]                | Applies an [aura] that "Casts" a meta-skill using various advanced options.                                                                                                    |
| [Chain][]               | Chains a skill between multiple targets that are near each other.                                                                                       |
| [ChainMissile][]        | A missile that chains between entities. **Premium-Only** mechanic!                                                                                      |
| [Delay][]               | Delays execution of the current skill list by a set number of ticks.                                                                                    |
| [DetermineCondition][]  | Determines the outcome of a Metaskill that is used as a Condition via the [MetaskillCondition](/Skills/Conditions/MetaskillCondition) condition                                                                                    |
| [EndProjectile][]       | Terminates the projectile. Only usable in projectile mechanics.                                                                                         |
| [ForEach][]             | Executes a metaskill once for each target of the mechanic                     |
| [ForEachValue][]        | Executes a metaskill once for each entry or key-value pair in the specified value                     |
| [ForEachPin][]        | Executes a metaskill once for each pin of a multi-pin                     |
| [GlobalCooldown][]      | Sets the caster's Global Cooldown timer                                                                                                                 |
| [Missile][]             | Fires a homing projectile towards the target.                                                                                                           |
| [ModifyProjectile][]    | Modifying the projectile / missile / orbital                                                                                                            |
| [OnAttack][]            | Applies an [aura][] to the target that triggers skills when they attack                                                                                 |
| [OnDamaged][]           | Applies an [aura][] to the target that triggers skills when they take damage                                                                            |
| [OnShoot][]             | Applies an [aura][] to the target that triggers skills when they shoot a bow                                                                            |
| [OnBlockBreak][]        | Applies an [aura][] to the target that triggers skills when they break a block                                                                          |
| [OnBlockPlace][]        | Applies an [aura][] to the target that triggers skills when they place a block                                                                          |
| [OnChat][]              | Applies an [aura][] to the target that triggers skills when they chat                                                                          |
| [OnSwing][]             | Applies an [aura][] to the target that triggers skills when they swing / left click                                                                     |
| [OnInteract][]          | Applies an [aura][] to the target that triggers skills when they interact / right click while holding a block or looking at an outlined block (NOT AIR) |
| [OnJump][]              | Applies an [aura][] to the target that triggers a skill when they jump (PAPER ONLY MECHANIC)                                                            |
| [OnDeath][]             | Applies an [aura][] to the target that triggers a skill when they die                                                                                   |
| [Orbital][]             | Applies an [aura][] that causes a projectile to orbit around the target                                                                                 |
| [FollowPath][]          | Applies an [aura][] that causes the mob to follow a path                                                                                 |
| [FormLine][]            | Applies an [aura][] that causes the mob to follow a *straight* path                                                                                 |
| [Polygon][]             | Creates a highly-customizable polygon-shaped pattern that can execute metaskills.                                                                                                                |
| [Projectile][]          | Fires a highly-customizable projectile towards the target                                                                                               |
| [ProjectileVelocity][]  | Modifies the velocity of the calling Projectile or Missile                                                                                               |
| [RandomSkill][]         | Executes a random skill from a list                                                                                                                     |
| [SetSkillCooldown][]    | Sets the given metakill's cooldown to the given value                                                                                                   |
| [SetProjectileDirection][]| Sets the calling projectile's movement direction to the given target                                            |
| [SetProjectileBulletModel][]    | Sets the model of the projectile. (DISPLAY bullets only)                                                                                                   |
| [Shoot][]               | Shoots a item-projectile at the target, similar to arrows/eggs/snowballs.                                                                               |
| [Slash][]               | Creates a highly-customizable slash pattern that can execute metaskills.                                                                               |
| [SudoSkill][]           | Makes the target execute a skill                                                                                                                        |
| [Switch][]              | Acts as a switch/case                                                                                                                                   |
| [StatAura][]            | Applies an aura to the target that applies a specific stat to them                                                                                                                                   |
| [Totem][]               | Creates a static "totem" at a location that can execute other skills                                                                                    |
| [Terminable][]          | Creates an [aura] that cancels the execution of its onStart metaskill is some conditions are met        |
| [Volley][]              | Shoots a volley of projectile-items at the target with various options                                                                                  |
| [VariableAdd][]         | Adds an amount to a numeric variable                                                                                                                    |
| [VariableMath][]        | Performs math on a numeric variable                                                                                                                     |
| [SetVariable][]         | Sets the value of a variable                                                                                                                            |
| [SetVariableLocation][] | Sets a variable to the target location                                                                                                                  |
| [VariableUnset][]       | Unsets the variable                                                                                                                                     |
| [VariableSubtract][]    | Subtracts an amount from a numeric variable                                                                                                             |
| [VariableMove][]        | Moves an already created variable across names and/or registries                                                                                                             |
| [Wait][]                | Puts the metaskill on hold until a set of conditions is met                                                                                                             |


# Universal Attributes

The following attributes are applicable to all mechanics.

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| cooldown  | cd        | In seconds. Allows for decimal values.                               | 0       |
| delay     |           | Delays the execution of the mechanic by a set number of ticks.       | 0       |
| repeat    |           | How many times the mechanic should be repeated. If repeatInterval is set to `0`, this becomes the number of executions rather than repetitions                                  | 0       |
| repeatInterval | repeatI | How many ticks must elapse between repetitions                    | 0       |
| targetInterval | targetI | How many ticks must elapse between target selection               | 0       |
| origin | | *[PREMIUM]** Change the origin to whatever targeter is supplied. Does not work if more than one target is parsed. `origin=@Forward{f=10}`<br>The targeter of the origin attribute will be parsed separately from the mechanic's targeter, so if you use something like `origin=@targetedlocation` it will not return the mechanic's explicit target, but the metaskill's inherited one  |   |
| power     |           | [Power](/mobs/Power) multiplier                                      | 1       |
| fromorigin | fo, sourceisorigin, castfromorigin | Whether to cast the mechanic from origin. This only works with a select few mechanics, and is usually listed as one of their attributes, too       | false   |
| targetisorigin |      | Whether to set the target of the mechanic to be the origin           | false   |
| targetcreative |      | Whether to target creative players                                   | false   |
| splitPower| powersplit, powersplitbetweentargets | Whether to split the power between targets| false   |
| faulty    |           | Whether the mechanic should use the old vector formula               | true    |
| chance    |           | The chance of the mechanic executing. For instance, 0.1 is a 10% chance | 1    |
| forcesync | sync      | Whether to force the mechanic to be run synchroniously with the main Minecraft thread. This *generally* worsens performances (albeit usually in a non-perceptible fashion), but **some mechanics needs this to be set to true** *(for instance, the [cancelevent] mechanic, since an event cannot be cancelled if the mechanics comes in "late" and the event has already happened)*             | false   |


# Examples
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - message{m="This message will only be shown once every 5 seconds!";cooldown=5} @trigger ~onInteract
  - message{m="This one 5 times in a row over 2 seconds!";repeat=4;repeatInterval=10} @trigger ~onInteract
```



<!--
Upcoming Mechanics
------------------

These mechanics are currently being worked on and will be in future
releases of the plugin. Some mechanics listed here are already included,
but not yet ready for use.

| Mechanic           | Description                     |
|--------------------|---------------------------------|
-->

  [AIGoalSelectors]: /Mobs/Custom-AI#ai-goal-selectors
  [AITargetSelectors]: /Mobs/Custom-AI#ai-target-selectors
  [here!]: /skills/skillparametersystem
  [Targeter]: /skills/targeters/

  [ActivateSpawner]: /skills/mechanics/activatespawner
  [AddTrade]: /skills/mechanics/AddTrade
  [AnimateArmorStand]: /skills/mechanics/animatearmorstand
  [ArmAnimation]: /skills/mechanics/ArmAnimation
  [ArrowVolley]: /skills/mechanics/arrowvolley
  [Attribute]: /skills/mechanics/Attribute
  [AttributeModifier]: /skills/mechanics/AttributeModifier
  [AuraRemove]: /skills/mechanics/auraremove
  [BarCreate]: /skills/mechanics/barcreate
  [BarSet]: /skills/mechanics/barset
  [BarRemove]: /skills/mechanics/barremove
  [Blackscreen]: /skills/mechanics/Blackscreen
  [BlockDestabilize]: /skills/mechanics/blockdestabilize
  [BlockMask]: /skills/mechanics/BlockMask
  [BlockUnmask]: /skills/mechanics/BlockUnmask
  [BlockPhysics]: /skills/mechanics/blockphysics
  [BlockWave]: /skills/mechanics/BlockWave
  [BloodyScreen]: /skills/mechanics/BloodyScreen
  [BoneMeal]: /skills/mechanics/bonemeal
  [BossBorder]: /skills/mechanics/bossborder
  [Bouncy]: /skills/mechanics/Bouncy
  [BreakBlock]: /skills/mechanics/breakblock
  [BreakBlockAndGiveItem]: /skills/mechanics/breakBlockAndGiveItem
  [ClearExperience]: /skills/mechanics/ClearExperience
  [ClearExperienceLevels]: /skills/mechanics/ClearExperienceLevels
  [ClearTarget]: /skills/mechanics/ClearTarget
  [GiveExperienceLevels]: /skills/mechanics/GiveExperienceLevels
  [TakeExperienceLevels]: /skills/mechanics/TakeExperienceLevels
  [CloseInventory]: /skills/mechanics/closeinventory
  [Command]: /skills/mechanics/command
  [Consume]: /skills/mechanics/consume
  [ConsumeSlot]: /skills/mechanics/consumeslot
  [DirectionalVelocity]: /skills/mechanics/DirectionalVelocity
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
  [PercentDamage]: /skills/mechanics/percentdamage
  [Decapitate]: /skills/mechanics/decapitate
  [Doppleganger]: /skills/mechanics/doppleganger
  [DropItem]: /skills/mechanics/dropitem
  [EjectPassenger]: /skills/mechanics/ejectpassenger
  [Ender]: /skills/mechanics/Ender
  [EnderBeam]: /skills/mechanics/EnderBeam
  [EnderDragonResetCrystals]: /Skills/Mechanics/EnderDragonResetCrystals
  [EnderDragonSetPhase]: /Skills/Mechanics/EnderDragonSetPhase
  [EnderDragonSetRespawnPhase]: /Skills/Mechanics/EnderDragonSetRespawnPhase
  [EnderDragonSpawnPortal]: /Skills/Mechanics/EnderDragonSpawnPortal
  [Equip]: /skills/mechanics/equip
  [EquipCopy]: /skills/mechanics/equipcopy
  [Explosion]: /skills/mechanics/explosion
  [FakeExplosion]: /skills/mechanics/FakeExplosion
  [Extinguish]: /skills/mechanics/extinguish
  [FawePaste]: /skills/mechanics/fawepaste
  [Feed]: /skills/mechanics/feed
  [Fear]: /skills/mechanics/Fear
  [FillChest]: /skills/mechanics/fillChest
  [Firework]: /skills/mechanics/firework
  [Flames]: /skills/mechanics/flames
  [Fly]: /skills/mechanics/fly
  [Freeze]: /skills/mechanics/freeze
  [ForcePull]: /skills/mechanics/forcepull
  [Geyser]: /skills/mechanics/geyser
  [Glow]: /skills/mechanics/glow
  [GiveItem]: /skills/mechanics/giveitem
  [GiveItemFromSlot]: /skills/mechanics/giveitemfromslot
  [GiveItemFromTarget]: /skills/mechanics/giveitemfromtarget
  [GoatRam]: /skills/mechanics/GoatRam
  [GoTo]: /skills/mechanics/goto
  [GuardianBeam]: /skills/mechanics/guardianbeam
  [Heal]: /skills/mechanics/heal
  [HealPercent]: /skills/mechanics/healpercent
  [Hide]: /skills/mechanics/hide
  [Hit]:  /skills/mechanics/hit 
  [Hologram]: /skills/mechanics/hologram
  [Ignite]: /skills/mechanics/ignite
  [ItemSpray]: /skills/mechanics/itemspray
  [JSONMessage]: /skills/mechanics/jsonmessage
  [Jump]: /skills/mechanics/jump
  [Leap]: /skills/mechanics/leap
  [Lightning]: /skills/mechanics/lightning
  [FakeLightning]: /skills/mechanics/FakeLightning
  [Log]: /skills/mechanics/Log
  [Look]: /skills/mechanics/look
  [Lunge]: /skills/mechanics/lunge
  [MatchRotation]: /skills/mechanics/MatchRotation
  [Message]: /skills/mechanics/message
  [ModifyDamage]: /skills/mechanics/ModifyDamage
  [ModifyGlobalScore]: /skills/mechanics/modifyglobalscore
  [ModifyTargetScore]: /skills/mechanics/modifytargetscore
  [ModifyMobScore]: /skills/mechanics/modifymobscore
  [ModifyScore]: /skills/mechanics/modifyscore
  [Mount]: /skills/mechanics/mount
  [MountMe]: /skills/mechanics/mountme
  [MountTarget]: /skills/mechanics/mounttarget
  [MovePin]: /skills/mechanics/MovePin
  [OpenCustomMenu]: /Skills/Mechanics/OpenCustomMenu
  [OpenTrades]: /skills/mechanics/OpenTrades
  [Oxygen]: /skills/mechanics/oxygen
  [Particle]: /skills/mechanics/Particle
  [ParticleBox]: /skills/mechanics/ParticleBox
  [ParticleEquation]: /skills/mechanics/ParticleEquation
  [ParticleLine]: /skills/mechanics/ParticleLine
  [ParticleLineHelix]: /skills/mechanics/ParticleLineHelix
  [ParticleLineRing]: /skills/mechanics/ParticleLineRing
  [ParticleOrbital]: /skills/mechanics/ParticleOrbital
  [ParticleRing]: /skills/mechanics/ParticleRing
  [ParticleSphere]: /skills/mechanics/ParticleSphere
  [ParticleTornado]: /skills/mechanics/ParticleTornado
  [Atom]: /skills/mechanics/Atom
  [PickUpItem]: /skills/mechanics/pickupitem
  [PlayAnimation]: /skills/mechanics/PlayAnimation
  [PlayBlockBreakSound]: /skills/mechanics/PlayBlockBreakSound
  [PlayBlockFallSound]: /skills/mechanics/PlayBlockFallSound
  [PlayBlockHitSound]: /skills/mechanics/PlayBlockHitSound
  [PlayBlockPlaceSound]: /skills/mechanics/PlayBlockPlaceSound
  [PlayBlockStepSound]: /skills/mechanics/PlayBlockStepSound
  [PoseArmorStand]: /skills/mechanics/posearmorstand
  [Potion]: /skills/mechanics/potion
  [PotionClear]: /skills/mechanics/potionclear
  [Prison]: /skills/mechanics/prison
  [PrintParentTree]: /skills/mechanics/PrintParentTree
  [Propel]: /skills/mechanics/propel
  [Pull]: /skills/mechanics/pull
  [PushBlock]: /skills/mechanics/PushBlock
  [PushButton]: /skills/mechanics/pushbutton
  [Rally]: /skills/mechanics/rally
  [RandomMessage]: /skills/mechanics/randommessage
  [Recoil]: /skills/mechanics/Recoil
  [Remount]: /skills/mechanics/remount
  [Remove]: /skills/mechanics/remove
  [RemoveHeldItem]: /skills/mechanics/removehelditem
  [RemoveOwner]: /skills/mechanics/removeowner
  [ResetAI]: /skills/mechanics/ResetAI
  [RotateTowards]: /skills/mechanics/RotateTowards
  [RunAIGoalSelector]: /skills/mechanics/runaigoalselector
  [RunAITargetSelector]: /skills/mechanics/runaitargetselector
  [Saddle]: /skills/mechanics/saddle
  [SendActionMessage]: /skills/mechanics/sendactionmessage
  [SendResourcePack]: /skills/mechanics/sendresourcepack
  [SendTitle]: /Skills/Mechanics/SendTitle
  [SendToast]: /skills/mechanics/sendtoast
  [SetAI]: /skills/mechanics/setai
  [SetBlockOpen]: /skills/mechanics/SetBlockOpen
  [SetBlockType]: /skills/mechanics/setblocktype
  [SetChunkForceLoaded]: /skills/mechanics/SetChunkForceLoaded
  [SetCollidable]: /skills/mechanics/setcollidable
  [SetCustomMenuButton]: /Skills/Mechanics/SetCustomMenuButton
  [SetDragonPodium]: /skills/mechanics/SetDragonPodium
  [SetFaction]: /skills/mechanics/setFaction
  [SetFlying]: /skills/mechanics/SetFlying
  [SetGameMode]: /skills/mechanics/setgamemode
  [SetGliding]: /skills/mechanics/setgliding
  [SetGlobalScore]: /skills/mechanics/setglobalscore
  [SetGravity]: /skills/mechanics/setgravity
  [SetHealth]: /skills/mechanics/sethealth
  [SetInteractionSize]: /skills/mechanics/SetInteractionSize
  [SetItemGroupCooldown]: /skills/mechanics/SetItemGroupCooldown
  [setDisplayEntityItem]: /skills/mechanics/setDisplayEntityItem
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
  [SetPathfindingMalus]: /skills/mechanics/SetPathfindingMalus
  [SetPitch]: /skills/mechanics/SetPitch
  [SetPose]: /skills/mechanics/SetPose
  [setRaiderCanJoinRaid]: /Skills/Mechanics/setRaiderCanJoinRaid
  [SetRaiderPatrolBlock]: /skills/mechanics/setraiderpatrolblock
  [SetRaiderPatrolLeader]: /skills/mechanics/setraiderpatrolleader
  [SetRotation]: /skills/mechanics/setrotation
  [SetTarget]: /skills/mechanics/settarget
  [SetTargetScore]: /skills/mechanics/settargetscore
  [SetTextDisplay]: /skills/mechanics/SetTextDisplay
  [SetTongueTarget]: /skills/mechanics/settonguetarget
  [SetScore]: /skills/mechanics/setscore
  [SetSpeed]: /skills/mechanics/setspeed
  [SetStance]: /skills/mechanics/setstance
  [Shield]: /skills/mechanics/shield
  [ShieldBreak]: /skills/mechanics/shieldbreak
  [ShieldPercent]: /skills/mechanics/shieldpercent
  [ShootFireball]: /skills/mechanics/shootfireball
  [ShootPotion]: /skills/mechanics/shootpotion
  [ShootSkull]: /skills/mechanics/shootskull
  [ShootShulkerBullet]: /skills/mechanics/shootshulkerbullet
  [ShowEntity]: /skills/mechanics/showentity
  [Signal]: /skills/mechanics/signal
  [Skybox]: /skills/mechanics/Skybox
  [Smoke]: /skills/mechanics/Smoke
  [SmokeSwirl]: /skills/mechanics/SmokeSwirl
  [Sound]: /skills/mechanics/Sound
  [StealItem]: /skills/mechanics/StealItem
  [StopSound]: /skills/mechanics/StopSound
  [Speak]: /skills/mechanics/speak
  [Spin]: /skills/mechanics/Spin
  [Spring]: /skills/mechanics/spring
  [StopUsingItem]: /skills/mechanics/stopusingitem
  [Stun]: /skills/mechanics/stun
  [Suicide]: /skills/mechanics/suicide
  [Summon]: /skills/mechanics/summon
  [SummonAreaEffectCloud]: /skills/mechanics/summonareaeffectcloud
  [SummonFallingBlock]: /skills/mechanics/SummonFallingBlock
  [SummonPassenger]: /skills/mechanics/summonpassenger
  [Swap]: /skills/mechanics/swap
  [SwingOffhand]: /skills/mechanics/SwingOffhand
  [AddTag]: /skills/mechanics/addtag
  [RemoveTag]: /skills/mechanics/removetag
  [TakeItem]: /skills/mechanics/takeitem
  [Taunt]: /skills/mechanics/Taunt
  [Teleport]: /skills/mechanics/teleport
  [TeleportY]: /skills/mechanics/teleporty
  [TeleportIn]: /skills/mechanics/teleportin
  [TeleportTo]: /skills/mechanics/teleportto
  [Threat]: /skills/mechanics/threat
  [Throw]: /skills/mechanics/throw
  [ThunderLevel]: /skills/mechanics/ThunderLevel
  [Time]: /skills/mechanics/time
  [ToggleLever]: /skills/mechanics/togglelever
  [TogglePiston]: /skills/mechanics/TogglePiston
  [ToggleSitting]: /skills/mechanics/togglesitting
  [TotemOfUndying]: /skills/mechanics/TotemOfUndying
  [TrackLocation]: /skills/mechanics/tracklocation
  [UndoPaste]: /skills/mechanics/undopaste
  [Velocity]: /skills/mechanics/velocity
  [Weather]: /skills/mechanics/weather
  [WolfSit]: /skills/mechanics/wolfsit
  [WorldEditReplace]: /skills/mechanics/WorldEditReplace
  
  <!-- METAMECHANICS -->
  [Skill]: /skills/mechanics/skill
  [VariableSkill]: /skills/mechanics/variableskill
  [Aura]: /skills/mechanics/aura
  [aura]: /skills/mechanics/aura
  [Beam]: /skills/mechanics/Beam
  [CancelEvent]: /skills/mechanics/cancelevent
  [CancelSkill]: /skills/mechanics/CancelSkill
  [Cast]: /skills/mechanics/cast
  [Chain]: /skills/mechanics/chain
  [ChainMissile]: /skills/mechanics/chainmissile
  [Delay]: /skills/mechanics/delay
  [DetermineCondition]: /skills/mechanics/DetermineCondition
  [EndProjectile]: /skills/mechanics/endprojectile
  [ForEach]: /skills/mechanics/ForEach
  [ForEachValue]: /skills/mechanics/ForEachValue
  [ForEachPin]: /skills/mechanics/ForEachPin
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
  [FollowPath]: /skills/mechanics/FollowPath
  [FormLine]: /skills/mechanics/FormLine
  [Polygon]: /skills/mechanics/polygon
  [Projectile]: /skills/mechanics/projectile
  [ProjectileVelocity]: /skills/mechanics/projectilevelocity
  [RayTrace]: /skills/mechanics/raytrace
  [RayTraceTo]: /skills/mechanics/raytraceto
  [Shoot]: /skills/mechanics/shoot
  [Slash]: /skills/mechanics/slash
  [Volley]: /skills/mechanics/volley
  [SudoSkill]: /skills/mechanics/sudoskill
  [RandomSkill]: /skills/mechanics/randomskill
  [SetSkillCooldown]: /skills/mechanics/setskillcooldown
  [SetProjectileDirection]: /skills/mechanics/SetProjectileDirection
  [SetProjectileBulletModel]: /skills/mechanics/setprojectilebulletmodel
  [StatAura]: /skills/mechanics/StatAura
  [Totem]: /skills/mechanics/totem
  [VariableAdd]: /skills/mechanics/variableadd
  [VariableMath]: /skills/mechanics/variablemath
  [SetVariable]: /skills/mechanics/setvariable
  [SetVariableLocation]: /skills/mechanics/setvariablelocation
  [VariableUnset]: /skills/mechanics/variableunset
  [VariableSubtract]: /skills/mechanics/variablesubtract
  [VariableMove]: /skills/mechanics/VariableMove
  [Terminable]: /skills/mechanics/terminable
  [OnBlockBreak]: /skills/mechanics/onblockbreak
  [OnBlockPlace]: /skills/mechanics/onblockplace
  [OnChat]: /skills/mechanics/OnChat
  [OnSwing]: /skills/mechanics/onswing
  [OnInteract]: /skills/mechanics/oninteract
  [OnJump]: /skills/mechanics/onjump
  [OnDeath]: /skills/mechanics/ondeath
  [Switch]: /skills/mechanics/Switch
  [Wait]: /skills/mechanics/Wait
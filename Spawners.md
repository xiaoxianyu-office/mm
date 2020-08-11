Spawners
========

Spawners allow you to define specific points in your worlds at which
your custom mob creations can spawn. They can with a variety of useful
options, conditions and built-in timers, cooldowns and warmups. Note
that in MythicSpawners you can only use the old conditions system. Here
can you find them: [Legacy Conditions](/conditions/legacyconditions)

You can create spawners directly ingame by using [Commands](/commands)
and by creating the a configuration file in the folder
*/MythicMobs/Spawners*. Note that once a spawner-configuration file has
been loaded onto a running server, it can only be edited by ingame
commands. If you want to edit a already loaded spawner-configuration
file in a text-editor, you have to stop the server in the meantime.

### Pros of Spawners

-   Doesn't require natural mob spawning to be enabled to work.
-   Allows for a much more specific and consistent implementation
    because you can specify exactly where and how each mob spawn.
-   Support timers, leashing and other features.
-   Good to populate small arenas or dungeons.

### Cons of Spawners

-   Setup can be time consuming especially for larger implementations.
-   Can become very difficult to manage if not planned out correctly.
-   Mobs need to be configured appropriately.
-   Despawn false isnt a option that is meant to be used in mythic
    spawners.

Example Config
--------------

    SpawnerName:
      MobName: mobTypeName 
      World: worldname
      SpawnerGroup: GroupName
      X: 0 
      Y: 0 
      Z: 0 
      Radius: 0 
      RadiusY: 0 
      UseTimer: true  
      MaxMobs: 1
      MobLevel: 1
      MobsPerSpawn: 1
      Cooldown: 0
      CooldownTimer: 0
      Warmup: 0
      WarmupTimer: 0
      CheckForPlayers: true
      ActivationRange: 40
      LeashRange: 32
      HealOnLeash: false
      ResetThreatOnLeash: false
      ShowFlames: false
      Breakable: false
      Conditions: []
      ActiveMobs: 1

Options
-------

-    **mobtype &lt;mobtype&gt;** or **mobname: &lt;mobtype&gt;:**
    -    This is mob type that the spawner will spawn. Can only be set
        to any internal MythicMobs mob.
    -    **/mm s set Ruins\_Skeleton1 mobtype GreaterSkeleton** (Changes
        the mobtype from DecayingSkeleton to GreaterSkeleton)
-    **world: &lt;worldname&gt;:**
    -    This is the filename of the world where the spawner is located
    -    **/mm s set Ruins\_Skeleton1 world survivalworld** (Changes the
        world where the spawner is located to survivalworld)
-    **spawnergroup: &lt;group name&gt;**
    -    This sets the group name for the spawn.
    -    For larger configurations, such as if you are populating a
        dungeon, you can group all spawners together and then change
        settings for them all at the same time. If you have 20 spawners,
        this is the difference between typing 2 or 3 commands and 20 or
        30 commands.
    -    \*\*/mm s set Ruins\_Skeleton1 group Ruins \*\*(Puts this
        spawner in the Ruins group)
    -    Using the group command:
        -    **/mm s set g:Ruins warmup 300**
        -    Sets the warmup settings for all spawners in the ruins
            group to 300
-    **X: / Y: / Z:**
    -    Coordinates of the spawner
-    **radius: &lt;number&gt;:**
    -    This is the radius around the spawner at which the mob can
        spawn. setting to 0 will cause the mob to spawn exactly on its
        spawner. Setting it to 5 will allow the mob to spawn anywhere
        within a 5 block radius of the spawner.
    -    This can be used to make mob spawns in large areas feel more
        random when large radius' are used.
    -    **/mm s set Ruins\_Skeleton1 radius 5** (Sets the spawner to
        spawn mobs within a 5 block radius)
-    **radiusY: &lt;number&gt;:**
    -    This is the vertical radius around the spawner at which the mob
        can spawn. setting to 0 will cause the mob to spawn exactly on
        its spawner's Y level. Setting it to 5 will allow the mob to
        spawn anywhere within a vertical 5 block radius of the spawner.
    -    This can be used to make mob spawns in large areas feel more
        random when large radius' are used.
    -    Defaults to 0
    -    **/mm s set Ruins\_Skeleton1 radiusy 5** (Sets the spawner to
        spawn mobs within a vertical 5 block radius)
-    **usetimer: &lt;true/false&gt;:**
    -    Whether or not the spawner activates on a timer. Set to false
        to activate on command only
    -    Defaults to true
-    **maxmobs: &lt;number&gt;:**
    -    This is the max number of mobs that can be spawned and existing
        in the world for this spawner. Should be set equal to or greater
        than the **mobsperspawn** settings.
    -    **/mm s set Ruins\_Skeleton1 maxmobs 2** (Sets the spawner to
        allow a maximum of 2 mobs to be spawned)
-    **moblevel: &lt;number&gt;:**
    -    This is the level of the mob that should spawn from this
        spawner. Mob must have level configuration for this to work. Can
        only be a single level.
    -    **/mm s set Ruins\_Skeleton1 moblevel 2** (Sets the spawner to
        spawn mobs of level 2)
-    **mobsperspawn: &lt;number&gt;:**
    -    This is the number of mobs spawned each time the spawner spawns
        a mob. This is limited by the **maxmobs** settings.
    -    **/mm s set Ruins\_Skeleton1 mobsperspawn 2** (Sets the spawner
        to spawn 2 mobs each time)
-    **cooldown: &lt;number&gt;:**
    -    This the amount of time in seconds that the spawner waits after
        a mob has been spawned before another mob is spawned.
    -    **/mm s set Ruins\_Skeleton1 cooldown 30** (Sets cooldown to 30
        seconds)
    -    Timing: warmup\*&gt; mob spawns\*&gt; cooldown\*&gt; mob
        spawns\*&gt;
-    **cooldowntimer: &lt;number&gt;:**
    -    This option is set automatically by the spawner, *it does not
        require any user setting*.
    -    Used to bridge cooldowns over server reboots.
-    **warmup: &lt;number&gt;:**
    -    The amount of time in seconds before the spawner start
        cooldown. Warmup start on activation and if maxmobs is reached
        and a mob dies.
    -    **/mm s set Ruins\_Skeleton1 warmup 300** (Sets warmup to 5
        minutes)
-    **warmuptimer: &lt;number&gt;:**
    -    This option is set automatically by the spawner, *it does not
        require any user setting*.
    -    Used to bridge warmups over server reboots.
-    **checkforplayers: &lt;true/false&gt;:**
    -    Whether or not players must be near the spawner for it to
        "activate"
    -    Defaults to true for performance
-    **activationrange: &lt;number&gt;:**
    -    What radius must players be within for the spawner to activate.
    -    Defaults to 40
-    **leashrange: &lt;number&gt;:**
    -    This is the max distance that a mob can move from its spawn
        location before it is teleported back to where it came from.
    -    \*\*/mm s set Ruins\_Skeleton1 leashrange 15 \*\*(Sets
        leashrange to 15 blocks)
-    **healonleash: &lt;true/false&gt;**
    -    Whether the mob should heal to full health when it leashes back
        to its spawner
    -    \*\*/mm s set Ruins\_Skeleton1 healonleash true \*\* (Mobs
        spawned from this spawner will heal on leash)
-    **resetthreatonleash: &lt;true/false&gt;**
    -    Resets ThreatTables (if enabled) when a mob teleports back to
        its spawner.
    -    Defaults to true
-    **showflames: &lt;true/false&gt;:**
    -    Set this to true to show flames around the spawner. Useful for
        debugging purposes.
    -    **/mm s set Ruins\_Skeleton1 showflames true** (Turn on flames
        particle for this spawner.)
-    **breakable: &lt;true/false&gt;:**
    -    *This entry needs clarification.*
-    **conditions:**
    -    Set conditions to be met for the spawner to activate.
    -    MythicSpawners can only use the legacy conditions system. Here
        can you find them: [Legacy
        Conditions](/conditions/legacyconditions)
-    **activemobs: &lt;number&gt;**
    -    This option is set automatically by the spawner, *it does not
        require any user setting*.
    -    Used to keep track of mobs connected to (spawned by) the
        spawner.

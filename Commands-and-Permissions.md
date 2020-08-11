Commands
========

Mythic Mobs has a simple command structure that can be accessed by
typing **/mythicmobs**. Typing that will display a menu with all
available commands, and each level of commands will provide menus or
information about what you can do. All command parameters surrounded by
\[\]'s are required, while &lt;&gt;'s are optional.

General Commands
----------------

-    **/mm** (alias: **/mythicmobs**) \* *Base command for the plugin.
    Displays all other commands.*
-    **/mm debug \[level\]** (alias: **/mm d \[level\]** \* *Sets the
    plugin's debug\*level. 0 = OFF.*
-    **/mm debugmode \[true/false\]** \* //Enables debug mode, which
    disables random spawners, mob spawners, and other random things that
    make debugging difficult. *Does not currently seem to work*//
-    **/mm reload** (alias: **/mm r**) \* *Reloads the plugin.*
-    **/mm save** \* *Force\*saved all active mobs and spawners.*
-    **/mm version** \* *Displays MythicMobs version.*

Item Commands
-------------

-    **/mm items** (alias: **/mm i**) \* *Base for all item\*related
    commands.*
-    **/mm items get \[item\_name\] &lt;amount&gt;** \* *Gives yourself
    an item from the configured mob equipment.*
-    **/mm items give \[player\] \[item\_name\] &lt;amount&gt;** \*
    *Gives a player an item from the configured mob equipment.*
-    **/mm items give -s \[player\] \[item\_name\] &lt;amount&gt;** \*
    *Silently gives a player an item from the configured mob equipment.*
-    **/mm items list** \* *Lists off all configured mob equipment.*
-    **/mm item import &lt;itemName&gt; \[fileName\]** \* *Imports held
    item to the Items folder. (File name defaults to
    &lt;itemName&gt;.yml)*

Mob Commands
------------

-    **/mm mobs** (alias: **/mm m**) \* *Base for all mob\*related
    commands.*
-    **/mm mobs info \[mob\_name\]** \* *Displays lots of information
    about a Mythic Mob.*
-    \*\*/mm mobs list \*\* \* *Displays a list of mobs loaded to the
    server.*
-    \*\*/mm mobs listactive \*\* \* *Displays a list of currently
    spawned mobs, and the number of each.*
-    **/mm mobs kill \[mob\_name\]** \* *Removes all Mythic Mobs with
    the provided name.*
-    **/mm mobs killall** \* *Removes all active Mythic Mobs.*
-    **/mm mobs killall -p** \* *Removes all persistent Mythic Mobs.*
-    **/mm mobs spawn \[mob\_name\]:&lt;level&gt; &lt;amount&gt;
    &lt;world,x,y,z&gt;** \* *Spawns mobs with the provided name.*
-    **/mm mobs spawn -s \[mob\_name\]:&lt;level&gt; &lt;amount&gt;
    &lt;world,x,y,z&gt;** \* *Silently spawns the mob in- no console
    text.*
-    \*\*/mm mobs stats \*\* \* *Displays useful information about how
    many mobs are loaded on the server. (Amounts)*

Mob Egg Commands
----------------

-    **/mm egg** (alias: **/mm e**) \* *Base for all egg\*related
    commands.*
-    **/mm egg get \[mob\_name\] &lt;amount&gt;** \* *Gives you mob eggs
    for the specified Mythic Mob.*
-    **/mm egg give \[player\] \[mob\_name\] &lt;amount&gt;** \* *Gives
    a player mob eggs for the specified Mythic Mob.*

Spawner Commands
----------------

-    Mob spawners can use special filters and wild cards in most
    commands in place of the spawner's name to run the command on
    multiple spawners.
    -   Use **g:group\_name** to run commands on a whole group of
        spawners.
    -   Use **r:radius** to run commands on all spawners within
        **radius** blocks
    -   Use **?** for a single-character wildcard: Running the command
        **/mm s set ?at leashrange 32** will set it on spawners named
        Cat, Rat, Fat, but not one named Matt.
    -   Use \*\*\*\*\* for any number of wildcard characters: Running
        the command **/mm s set T\* leashrange 32** will set the leash
        range to 32 on all spawners starting with T
    -   \*\* Running the command using \* for the spawner name will
        change ALL spawners\*\*

<!-- -->

-    **/mm spawners** (alias: **/mm s**) \* *Base for all
    spawner\*related commands.*
-    **/mm s create** *\[*spawner*\_*name*\]* *\[*mob name*\]*
    -    Creates a new spawner at the location of the players reticule.
    -    The spawner will spawner whatever mob*\_*name you gave it which
        can be any internal minecraft mob or the name of a mob you
        created under the ExampleMobs.yml configuration page.
    -    **/mm s create Ruins*\_*Skeleton1 DecayingSkeleton**
-    **/mm s set \[spawner\_name\] \[setting\] \[value\]**
    -    Changes a setting of the spawner. See below for all settings
    -    See [Spawner Options Section](Databases/Spawners/Spawners) for
        all the things that can be set here.
-    **/mm s addcondition \[spawner\_name\] \[condition\] \[value\]**
    -    Adds a spawner condition which determines whether a mob should
        spawn when it's timer is up.
    -    See [Spawner Conditions](Databases/Spawners/Conditions) for
        conditions that can be applied here
-    \*\*/mm s removecondition \[spawner\_name\] \[condition\] \*\*
    -    Removes a spawner condition.
    -    **/mm s removecondition Ruins\_Skeleton1 outside**
-    **/mm s info \[spawner\_name\]**
    -    Provides a list of information about a particular spawner.
    -    \*\*/mm s info Ruins\_Skeleton1 \*\*(Lists information about
        the Ruins\_Skeleton1 spawner)
-    **/mm s listnear &lt;distance&gt;**
    -    Lists all spawners nearby.
    -    Add a the distance parameter to narrow the list down.
    -    **/mm s listnear 15** (Displays all the spawner names within 15
        blocks)
-    **/mm s resettimers \[name\]**
    -    Resets cooldown and reset timers for the spawner listed.
    -    **/mm s resettimers Ruins\_Skeleton1** (Resets the
        Ruins\_Skeleton1 spawner)
-    **/mm s activate \[name\]**
    -    Activates (forces a spawn from) a particular mob spawner.
    -    **/mm s activate Ruins\_Skeleton1** (Spawns the
        Ruins\_Skeleton1 spawner)
-    **/mm s cut \[search\_string\]**
    -    Cuts a group of spawners according to a given string.
    -    \*\*/mm s cut g:BoneCastle (Cuts all spawners in the
        "BoneCastle" spawner group)
    -    \*\*/mm s cut r:200 (Cuts all spawners in a 200 block radius)
    -    \*\*/mm s cut Elementals\_\* (Cuts all spawners whos name
        starts with Elementals\_)
    -    \*\*/mm s cut \* (Cuts all spawners. BE VERY CAREFUL!)
-    **/mm s paste**
    -    Pastes a group of cut spawners in a new relative location.
    -    Spawners can be pasted multiple times but replace previous
        pastes. (They are not duplicated)
-    **/mm s undo**
    -    Undoes the previous cut operation and puts them back where they
        were.
    -    Will only work if you have not yet cut a new group of spawners.

Utility Commands
----------------

-    **/mm u testeffect \[effect syntax\]**
    -    Allows you to run an effect as if you were the mob.
    -    Takes the same effect syntax that you would normally place
        inside your skill.
    -    **/mm u testeffect target particles
        witchMagic:1:1:100:0.01:1:0.5 &gt;0 1** (This is outdated)
-    **/mm u testskill \[targetlocation\] \[skillname\]** **(Does not
    currently work)**
    -    Allows you to run a skill as if you were the mob.
    -    Target can be any of the target locations. (target, boss,
        playersinradius, etc)
    -    Skill name should be the name of one of your skills.
    -    **/mm u testskill target lightning**

Signal Commands
---------------

-   **/mm signal &lt;UUID&gt; &lt;signal&gt;**
    -   Used to signal mobs to toggle certain skills
    -   Only works when used with the mobs UUID, doesnt work with
        mobnames
    -   Usually used as a tellraw-command component
    -   This command is available to all players. However players cannot
        abuse this command unless they have the operator powers
        neccessary to find specific mob UUIDs and internal signal names
        of mobs.

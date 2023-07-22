# Placeholders
------------

These are all of the placeholders and special characters you can use in
skills and mechanics that use strings. There are some examples of usage at the bottom to get you started.

__**Note:** Usage of many variables in skills are locked to the premium versions, excluding MMOCore, special characters, color codes, and `setvariable`__.

Special Characters
------------------

| **Placeholder** | **Function**                      |
|:---------------:|-----------------------------------|
|      <&co>      | Returns a colon (:)               |
|      <&sq>      | Returns an apostrophe (')         |
|      <&da>      | Returns a dash (-)                |
|      <&bs>      | Returns a backslash (\\)          |
|      <&fs>      | Returns a forward slash (/)       |
|      <&sp>      | Returns a space                   |
|      <&cm>      | Returns a comma (,)               |
|      <&sc>      | Returns a semicolon (;)           |
|      <&eq>      | Returns an equals symbol \[=\]    |
|      <&ss>      | Returns a section symbol (ยง)     |
|      <&dq>      | Returns double quotes (")         |
|      <&rb>      | Returns a right bracket (\])      |
|      <&lb>      | Returns a left bracket (\[)       |
|      <&rc>      | Returns a right curly bracket (}) |
|      <&lc>      | Returns a left curly bracket ({)  |
|      <&nm>      | Returns a number sign (#)         |
|      <&nl>      | Forces a new line                 |
|    <&heart>     | Returns a heart                   |
|    <&skull>     | Returns a skull and bones         |

Color Codes
-----------
These color codes work anywhere in mob- and skill-files. They will even
properly format tellraw-commands used in command skills! 

Legacy color codes:

| **Code** |  **Color**  | **Code** |   **Color**    |
|:--------:|:-----------:|:--------:|:--------------:|
|    &0    |    Black    |    &B    |      Aqua      |
|    &1    |  Dark Blue  |    &C    |      Red       |
|    &2    | Dark Green  |    &D    |  Light Purple  |
|    &3    |  Dark Aqua  |    &E    |     Yellow     |
|    &4    |  Dark Red   |    &F    |     White      |
|    &5    | Dark Purple |    &K    |     Magic      |
|    &6    |    Gold     |    &L    |      Bold      |
|    &7    |    Gray     |    &M    | Strike through |
|    &8    |  Dark Gray  |    &N    |   Underline    |
|    &9    |    Blue     |    &O    |     Italic     |
|    &A    |    Green    |    &R    |     Reset      |

As of MM 5.0.1+, it's recommended that you use [MiniMessage tags](https://docs.adventure.kyori.net/minimessage/format.html#standard-tags) for text styling and text decorations.
Here's an example using MiniMessage tags:
```yml
MessageSkill:
  Skills:
    - message{m=<rainbow>This text is a rainbow</rainbow> but <red>this is red</red>!} @target
    - message{m=<#bae5f4>This is a cool color that I picked from</#bae5f4> <red><click:open_url:https://www.color-hex.com/color/bae5f4>color-hex site</click></red>} @target
```
MiniMessage also has a [web viewer](https://webui.adventure.kyori.net/) to see what your text will look like in game.

Caster Placeholders
------------------
These placeholders will return whatever attribute of the caster that is called. For instance `<caster.l.y.#>` will return the caster's Y location.

|         Caster Placeholder         | Function                                                          |
|:----------------------------------:|-------------------------------------------------------------------|
|       <caster.damage>              | Returns the caster's Attack_Damage attribute value                |
|      <caster.display>              | Returns the caster's displayed name                               |
|      <caster.mythic_type>          | Returns the caster's internal mob type                            |
|        <caster.uuid>               | Returns the UUID of the caster                                    |
|       <caster.level>               | Returns the level of the caster                                   |
|        <caster.name>               | Returns the name of the caster                                    |
|         <caster.hp>                | Returns current hp of the caster                                  |
|        <caster.mhp>                | Returns the max hp of the caster                                  |
|        <caster.php>                | Returns the percent hp of the caster                              |
|        <caster.thp>                | Returns the full number hp of the caster                          |
|       <caster.tt.top>              | Returns the name of the top threat holder of the caster           |
|        <caster.l.w>                | Returns the world name the caster is in                           |
|        <caster.l.x>                | Returns the X coordinate of the caster                            |
|       <caster.l.x.#>               | Returns the X coordinate of the caster +- random number between # |
|     <caster.l.x.double>            | Returns the precise X coordinate of the caster                    |
|        <caster.l.y>                | Returns the Y coordinate of the caster                            |
|       <caster.l.y.#>               | Returns the Y coordinate of the caster +- random number between # |
|     <caster.l.y.double>            | Returns the precise Y coordinate of the caster                    |
|        <caster.l.z>                | Returns the Z coordinate of the caster                            |
|       <caster.l.z.#>               | Returns the Z coordinate of the caster +- random number between # |
|     <caster.l.z.double>            | Returns the precise Z coordinate of the caster                    |
|       <caster.l.yaw>               | Returns the yaw of the caster                                     |
|      <caster.l.pitch>              | Returns the pitch of the caster                                   |
|       <caster.stance>              | Returns the current stance of the caster                          |
|     <caster.owner.name>            | Returns the name of the wolf's owner                              |
|     <caster.owner.uuid>            | Returns the uuid of the wolf's owner                              |
| <caster.heldenchantlevel.#>        | Returns the enchant level of specified # enchant                  |
| <caster.skill.\[skill_name\].cooldown> | Returns the current cooldown of the give skill as a float number |
| <caster.raytrace>                  | Returns the name of the block being looked at by the caster (4.5 blocks of range) |
| <caster.children.size>             | Returns the number of children this entity has                    |

**Variable Placeholders**
-----------------
These placeholders will return whatever variable has been called. For instance <caster.var.\[name\]> will return the value of the caster's \[name\] variable.

| **Variable Placeholder**  | **Function**                                                            |     
|:-------------------------:|-------------------------------------------------------------------------|
|   <caster.var.\[name\]>   | Returns the value of the variable \[name\] on the caster.               |
|   <caster.stat.STAT_NAME>   | Returns the value of the specified stat on the caster.               |
|   <skill.var.\[name\]>    | Returns the value of the variable \[name\] on the current skill tree.   |
| <skill.var.damage-amount> | Returns the amount of damage taken in the onDamaged trigger             |
|  <skill.var.damage-type>  | Returns the type of damage taken as specified in a mechanic, aura, etc. |
|   <skill.var.aura-name>   | Returns the name of the aura as specified in an aura.                   |
| <skill.var.aura-charges>  | Returns the amount of charges the aura has left.                        |
| <skill.var.aura-duration> | Returns the duration of the aura.                                       |
|  <skill.var.aura-stacks>  | Returns the amount of stacks the aura has.                              |
|      <skill.targets>      | Returns the amount of inherited targets                                 |
| <skill.var.interval>      | Returns the interval value in mechanics using repeat & repeatInterval options|

**Target Placeholders**
-----------------
These placeholders will return whatever target selector has been used. For instance <target.name> + @NearestPlayer will return the name of the player closest to the casting mob. The following are only some of the placeholders that can have a `target` scope, and in general any placeholder that is also present in the [Caster Placeholder](#caster-placeholders) section will also work.

| **Target Placeholders** | **Function**                                                      |
|:-----------------------:|-------------------------------------------------------------------|
|      <target.uuid>      | Returns the UUID of the target                                    |
|      <target.name>      | Returns the name of the target                                    |
|       <target.hp>       | Returns current hp of the target                                  |
|      <target.mhp>       | Returns the max hp of the target                                  |
|      <target.php>       | Returns the percent hp of the target                              |
|      <target.thp>       | Returns the full number hp of the target                          |
|     <target.threat>     | Returns the threat level of the target                            |
|      <target.l.w>       | Returns the world name the target is in                           |
|      <target.l.x>       | Returns the X coordinate of the target                            |
|     <target.l.x.#>      | Returns the X coordinate of the target +- random number between # |
|      <target.l.y>       | Returns the Y coordinate of the target                            |
|     <target.l.y.#>      | Returns the Y coordinate of the target +- random number between # |
|      <target.l.z>       | Returns the Z coordinate of the target                            |
|     <target.l.z.#>      | Returns the Z coordinate of the target +- random number between # |
|     <target.l.yaw>      | Returns the yaw of the target                                     |
|    <target.l.pitch>     | Returns the pitch of the target                                   |
|     <target.level>      | Returns the level of the target                                   |
|   <target.block.type>   | Returns the block type of the target                              |
|   <target.block.data>   | Returns the block data of the target block                             |
|  <target.entity_type>   | Returns the entity type of the target                             |
|  <target.itemstack_amount>   | Returns the amount of item entities on the ground                             |
|   <target.raytrace>     | Returns the name of the block being looked at by the target (4.5 blocks of range) |

**Trigger Placeholders**
-----------------
These placeholders will return whatever attribute of the entity that caused the skill to happen. For instance `<trigger.name>` combined with an `~onDeath` trigger will return the name of the entity that killed the mob.

    Skills:
    - message{m="<&b><caster.name><&r> was slain by <&a><trigger.name><&r>."} @PIR{r=20} ~onDeath

The following are only some of the placeholders that can have a `trigger` scope, and in general any placeholder that is also present in the [Caster Placeholder](#caster-placeholders) section will also work.


-----------------
| Trigger Placeholders | Function                                                                               |
|:--------------------:|----------------------------------------------------------------------------------------|
|    <trigger.uuid>    | Returns the UUID of the entity triggering the skill                                    |
|    <trigger.name>    | Returns the name of the entity triggering the skill                                    |
|     <trigger.hp>     | Returns the current hp of the entity triggering the skill                              |
|    <trigger.mhp>     | Returns the max hp of the entity triggering the skill                                 |
|   <trigger.threat>   | Returns the threat level of the entity triggering the skill                            |
|    <trigger.l.w>     | Returns the world name of the entity triggering the skill                              |
|    <trigger.l.x>     | Returns the X coordinate of the entity triggering the skill                            |
|   <trigger.l.x.#>    | Returns the X coordinate of the entity triggering the skill +- random number between # |
|    <trigger.l.y>     | Returns the Y coordinate of the entity triggering the skill                            |
|   <trigger.l.y.#>    | Returns the Y coordinate of the entity triggering the skill +- random number between # |
|    <trigger.l.z>     | Returns the Z coordinate of the entity triggering the skill                            |
|   <trigger.l.z.#>    | Returns the Z coordinate of the entity triggering the skill +- random number between # |
|   <trigger.l.yaw>    | Returns the yaw of the trigger                                                         |
|  <trigger.l.pitch>   | Returns the pitch of the trigger                                                       |
|   <trigger.raytrace>     | Returns the name of the block being looked at by the trigger (4.5 blocks of range) |


Misc Placeholders
-----------------

|    **Placeholder**    | **Function**                                        |
|:---------------------:|-----------------------------------------------------|
|      <drops.xp>       | Returns the xp dropped via Heroes or SkillAPI mods  |
|     <drops.money>     | Returns the money dropped through the vault plug-in |

Special Placeholders
--------------------

| **Placeholder**             | **Function**                                                            |
|-----------------------------|-------------------------------------------------------------------------|
| <caster.score.objective>    | Returns the score of the caster from "objective"                        |
| <target.score.objective>    | Returns the targeters score from "objective"                            |
| <trigger.score.objective>   | Returns the score of the trigger from "objective"                       |
| <global.score.objective>    | Returns the score of fake player: \_\_GLOBAL\_\_ score from "objective" |
| <score.objective.player>    | Returns the score of the defined player from "objective"                |
| <score.objective.dummyname> | Returns the score of "dummyname" (fake player) from "objective"         |
| <random.#to#>               | Returns a random integer in the specified range                         |
| <random.float.#to#>         | Returns a random float number in the specified range                    |


## PlaceholderAPI Integration
Other than being able to use PlaceholderAPI placeholders anywhere placeholder support is in place, MythicMobs introduces some new PAPI placeholders that can be used by third parties to fetch MythicMobs-related values.
| **PAPI Placeholder**        | **Function**                                                            |
|-----------------------------|-------------------------------------------------------------------------|
| %mythic_var_someVar%        | Returns the value of the `someVar` variable that is set on the player   |
| %mythic_var_world_someVar%  | Returns the value of the `someVar` variable that is set on the world    |
| %mythic_var_global_someVar% | Returns the value of the `someVar` variable that is set on the server   |
| %mythic_var_<playerName>_someVar% | Returns the value of the `someVar` variable that is set on the specified player, by their name |
| %mythic_var_<UUID>_someVar% | Returns the value of the `someVar` variable that is set on the specified entity, by its UUID|


Examples
--------------------

**This will make a mob send a teal message to all players in a radius of 20 blocks around in itself, stating what entity killed it in green.**

```
    Skills:
    - message{m="<&b><caster.name><&r> was slain by <&a><trigger.name><&r>."} @PIR{r=20} ~onDeath
```

**This skill will make an announcement when the mob spawns that looks like this:**

![image](uploads/91ed6d8aaa669e8ae21f8745e8ff4643/image.png)

```
  Skills:
  - Skill{s=SaveBossLocation} @self ~onSpawn
  - message{m="&eA &BGiant Zombie&e (Level &4<caster.level>&e) &ehas spawned at <caster.var.SpawnLoc>"} ~onSpawn @PlayersInWorld
  - message{m="&eThe &BGiant Zombie&e (Level &4<caster.level>&e) &espawned at <caster.var.SpawnLoc>&e has been slain."} ~onDeath @PlayersInWorld
```

Be sure to place this skill somewhere in the skills file

```
SaveBossLocation:
  Skills:
  - setvariable{var=SpawnLoc;type=STRING;value="&b<caster.l.x>&e, &b<caster.l.y>&e, &b<caster.l.z>";scope=CASTER} @self
```
**You can also use color tags and formatting tags to make the mobs have pretty names:**

![image](uploads/9ad97422803c3f35fbeac2e4df7f7d52/image.png)

```
ZOMBIE:
  Display: 'ZOMBIE &F- &A<caster.hp>/<caster.mhp>HP &F- &ELv.<caster.level>'
```
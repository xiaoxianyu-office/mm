These are all of the placeholders and special characters you can use in
skills and mechanics that use strings. There are some examples of usage at the bottom to get you started.

__**Note:** Usage of many variables in skills are locked to the premium versions, excluding MMOCore, special characters, color codes, and `setvariable`__.


[[_TOC_]]

# Special Characters
| **Placeholder** | **Function**                                                               | Symbol  |
|:---------------:|----------------------------------------------------------------------------|---------|
|      <&co>      | Returns a colon                                                            | `:`     |
|      <&sq>      | Returns an apostrophe                                                      | `'`     |
|      <&da>      | Returns a dash                                                             | `-`     |
|      <&bs>      | Returns a backslash                                                        | `\`     |
|      <&fs>      | Returns a forward slash                                                    | `/`     |
|      <&sp>      | Returns a space                                                            | ` `     |
|      <&cm>      | Returns a comma                                                            | `,`     |
|      <&sc>      | Returns a semicolon                                                        | `;`     |
|      <&eq>      | Returns an equals symbol                                                   | `=`     |
|      <&dq>      | Returns double quotes                                                      | `"`     |
|      <&rb>      | Returns a right bracket                                                    | `]`     |
|      <&lb>      | Returns a left bracket                                                     | `[`     |
|      <&rc>      | Returns a right curly bracket                                              | `}`     |
|      <&lc>      | Returns a left curly bracket                                               | `{`     |
|      <&nm>      | Returns a number sign                                                      | `#`     |
|      <&nl>      | Forces a new line                                                          |  <br>   |
|    <&heart>     | Returns a heart                                                            | `❤`    |
|    <&skull>     | Returns a skull and bones                                                  | `☠`    |
|    <&lt>        | Returns the less than symbol                                               | `<`     |
|    <&gt>        | Returns the greater than symbol                                            | `>`     |
|   <^dot>        | Returns a dot                                                              | `.`     |
|   <^dot2>       | Returns the placeholder that returns a dot. Useful when there is sensitive placeholder parsing involved | `<^dot>`     |

# Color Codes
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

It's recommended that you use [MiniMessage tags](https://docs.adventure.kyori.net/minimessage/format.html#standard-tags) for text styling and text decorations.
Here's an example using MiniMessage tags:
```yml
MessageSkill:
  Skills:
    - message{m=<rainbow>This text is a rainbow</rainbow> but <red>this is red</red>!} @target
    - message{m=<#bae5f4>This is a cool color that I picked from</#bae5f4> <red><click:open_url:https://www.color-hex.com/color/bae5f4>color-hex site</click></red>} @target
```
MiniMessage also has a [web viewer](https://webui.adventure.kyori.net/) to see what your text will look like in game.

# Additional Placeholders
Links to placeholders added by addon plugins. Any placeholders from these links will not work without that plugin installed.

- [Mythic Crucible](https://git.mythiccraft.io/mythiccraft/mythiccrucible/-/wikis/Placeholders)
- [MCPets](https://mcpets.gitbook.io/mcpets/tutorials/mythicmobs-features#placeholders)

# Placeholders

## Caster Placeholders
These placeholders will return whatever attribute of the caster that is called. For instance `<caster.l.y.#>` will return the caster's Y location.

|         Caster Placeholder         | Function                                                          |
|:----------------------------------:|-------------------------------------------------------------------|
|       <caster.damage>              | Returns the caster's Attack_Damage attribute value                |
|      <caster.display>              | Returns the caster's displayed name                               |
|      <caster.mythic_type>          | Returns the caster's internal mob type                            |
|      <caster.type>                 |Returns the internal id of a MythicMob or the entity name otherwise|
|      <caster.type.name>           |Returns the display name of a MythicMob or the entity name otherwise|
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
|       <caster.l.x.{Float}>       | Returns the X coordinate of the caster +- random number between {Float} |
|     <caster.l.x.double>            | Returns the precise X coordinate of the caster                    |
|        <caster.l.y>                | Returns the Y coordinate of the caster                            |
|       <caster.l.y.{Float}>         | Returns the Y coordinate of the caster +- random number between {Float} |
|     <caster.l.y.double>            | Returns the precise Y coordinate of the caster                    |
|        <caster.l.z>                | Returns the Z coordinate of the caster                            |
|       <caster.l.z.{Float}>               | Returns the Z coordinate of the caster +- random number between {Float} |
|     <caster.l.z.double>            | Returns the precise Z coordinate of the caster                    |
|       <caster.l.yaw>               | Returns the yaw of the caster                                     |
|      <caster.l.pitch>              | Returns the pitch of the caster                                   |
|       <caster.stance>              | Returns the current stance of the caster                          |
| <caster.stat.{Stat}>               | Returns the value of the specified {Stat} on the caster           |
| <caster.heldenchantlevel.{Integer}>    | Returns the enchant level of specified {Integer} enchant      |
| <caster.skill.{Metaskill}.cooldown> | Returns the current cooldown of the give skill as a float number |
| <caster.raytrace.{Float}>                | Returns the name of the block being looked at by the caster if within {Float} range, if {Float} is specified. If only <caster.raytrace> is used, then the range defaults to `4.5`. If no block is found, `AIR` is returned.|
| <caster.children.size>             | Returns the number of children this entity has                    |
| <caster.attack_cooldown>           | Returns the attack cooldown of the player's equipped item. The value will be a float between 0 (maximum cooldown for the item) and 1 (no cooldown) |

## Target Placeholders
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
|     <target.l.x.{Float}> | Returns the X coordinate of the target +- random number between {Float} |
|      <target.l.y>       | Returns the Y coordinate of the target                            |
|     <target.l.y.{Float}> | Returns the Y coordinate of the target +- random number between {Float}|
|      <target.l.z>       | Returns the Z coordinate of the target                            |
|     <target.l.z.{Float}> | Returns the Z coordinate of the target +- random number between {Float} |
|     <target.l.yaw>      | Returns the yaw of the target                                     |
|    <target.l.pitch>     | Returns the pitch of the target                                   |
|     <target.level>      | Returns the level of the target                                   |
|   <target.block.type>   | Returns the block type of the target                              |
|   <target.block.data>   | Returns the block data of the target block                        |
|  <target.entity_type>   | Returns the entity type of the target                             |
|  <target.item.type>     | Returns the type of the targeted item entity                      |
|  <target.held.item>     | Returns the item held by the target                               |
|  <target.itemstack_amount>   | Returns the amount of item entities on the ground            |
| <target.stat.{StatName}> | Returns the value of the specified stat on the target             |
| <target.raytrace.{Float}> | Returns the name of the block being looked at by the target if within {Float} range, if {Float} is specified. If only <target.raytrace> is used, then the range defaults to `4.5`. If no block is found, `AIR` is returned.|
| <target.fovoffset{rotation=0;absolute=true}> | Returns the angular offset (in degrees) between the direction the caster is looking and the direction from the caster to the target entity. This offset can be used to determine how far the target is from the caster's center of view |
| <target.distance>       | Return the distance between the caster and the mechanic's target. If the target cannot be found in the caster's world, returns the maximum double value |
| <target.distancesquared> | Return the squared distance between the caster and the mechanic's target. If the target cannot be found in the caster's world, returns the maximum double value |
| <target.armor>          | Returns the target's armor value                                  | 
| <target.item.itemstack.{EquipSlot}> | Returns the ItemStack of the item in the specified slot on the target player. The slot can either be a named one (HAND, OFFHAND etc.) or a number |

## Trigger Placeholders
These placeholders will return whatever attribute of the entity that caused the skill to happen. For instance `<trigger.name>` combined with an `~onDeath` trigger will return the name of the entity that killed the mob.

```yaml
    Skills:
    - message{m="<&b><caster.name><&r> was slain by <&a><trigger.name><&r>."} @PIR{r=20} ~onDeath
```

The following are only some of the placeholders that can have a `trigger` scope, and in general any placeholder that is also present in the [Caster Placeholder](#caster-placeholders) section will also work.


| Trigger Placeholders | Function                                                                               |
|:--------------------:|----------------------------------------------------------------------------------------|
|    <trigger.uuid>    | Returns the UUID of the entity triggering the skill                                    |
|    <trigger.name>    | Returns the name of the entity triggering the skill                                    |
|     <trigger.hp>     | Returns the current hp of the entity triggering the skill                              |
|    <trigger.mhp>     | Returns the max hp of the entity triggering the skill                                 |
|   <trigger.threat>   | Returns the threat level of the entity triggering the skill                            |
|    <trigger.l.w>     | Returns the world name of the entity triggering the skill                              |
|    <trigger.l.x>     | Returns the X coordinate of the entity triggering the skill                            |
|   <trigger.l.x.{Float}>    | Returns the X coordinate of the entity triggering the skill +- random number between {Float} |
|    <trigger.l.y>     | Returns the Y coordinate of the entity triggering the skill                            |
|   <trigger.l.y.{Float}>    | Returns the Y coordinate of the entity triggering the skill +- random number between {Float} |
|    <trigger.l.z>     | Returns the Z coordinate of the entity triggering the skill                            |
|   <trigger.l.z.{Float}>    | Returns the Z coordinate of the entity triggering the skill +- random number between {Float} |
|   <trigger.l.yaw>    | Returns the yaw of the trigger                                                         |
|  <trigger.l.pitch>   | Returns the pitch of the trigger                                                       |
|  <trigger.held.item>   | Returns the item held by the trigger                                                      |
|   <trigger.raytrace>     | Returns the name of the block being looked at by the trigger (4.5 blocks of range) |
| <trigger.item.amount> | Returns the amount of the item the trigger is holding                                            |
| <trigger.item.type> | Returns the type of the item the trigger is holding                                            |
| <trigger.item.model> | Returns the model of the item the trigger is holding                                            |
| <trigger.stat.{Stat}> | Returns the value of the specified stat on the trigger                       |
| <trigger.raytrace.{Float}>                | Returns the name of the block being looked at by the trigger if within {Float} range, if # is specified. If only <trigger.raytrace> is used, then the range defaults to `4.5`. If no block is found, `AIR` is returned.|
| <trigger.distance>       | Return the distance between the caster and the skilltree's trigger. If the trigger cannot be found in the caster's world, returns the maximum double value |
| <trigger.distancesquared> | Return the squared distance between the caster and the skilltree's trigger. If the target cannot be found in the caster's world, returns the maximum double value |


## Misc Placeholders
|    **Placeholder**          | **Function**                                                            |
|-----------------------------|-------------------------------------------------------------------------|
| <drop.amount>               | Returns the amount dropped while used in specific drop types            |
| <drops.xp>                  | Returns the xp dropped via specific drop types                          |
| <drops.money>               | Returns the money dropped through the vault plug-in                     |
| <random.#to#>               | Returns a random integer in the specified range                         |
| <random.float.#to#>         | Returns a random float number in the specified range                    |
| <utils.epoch>               | Returns the current epoch                                               |
| <utils.epoch.seconds>       | Returns the current epoch                                               |
| <utils.epoch.timestamp>     | Returns the amount of milliseconds elapsed since the epoch              |
| <utils.epoch.millis>        | Returns the amount of milliseconds of the current epoch                 |
| <utils.epoch.ticks>         | Returns the current epoch, converted in ticks. Assumes that the server always maintains 20 ticks per second. Accounts for milliseconds. <br>While unorthodox, since time within Minecraft (and by extension Mythic) is measured in ticks, this may be of some help streamlining some processes where converting the normal epoch time to accomodate for ticks may be burdensome if done at scale |

## Item Placeholders
| **Placeholder**             | **Function**                                                            |
|-----------------------------|-------------------------------------------------------------------------|
| <item.amount>               | Returns the amount of the item that triggered the skill                 |
| <mythicitem.{MythicItem}.material>| Returns the material of the specified mythic item                 |
| <mythicitem.{MythicItem}.model>   | Returns the custommodeldata of the specified mythic item          |
| <mythicitem.{MythicItem}.display> | Returns the display name of the specified mythic item             |

## Score Placeholders
| **Placeholder**             | **Function**                                                            |
|-----------------------------|-------------------------------------------------------------------------|
| <caster.score.{Objective}>  | Returns the score of the caster from "{Objective}"                      |
| <target.score.{Objective}>  | Returns the targeters score from "{Objective}"                          |
| <trigger.score.{Objective}> | Returns the score of the trigger from "{Objective}"                     |
| <global.score.{Objective}>  | Returns the score of fake player: \_\_GLOBAL\_\_ score from "{Objective}" |
| <score.objective.player>    | Returns the score of the defined player from "objective"                |
| <score.objective.dummyname> | Returns the score of "dummyname" (fake player) from "objective"         |

```yaml
  - message{m=You have slain <trigger.var.slainmobs> Mobs!} @trigger ~onInteract
```

## Variable Placeholders
These placeholders will return whatever variable has been called. For instance <caster.var.\[name\]> will return the value of the caster's \[name\] variable.  
Some of these variables are only generated and available under some special circumstances, such as some specific trigger/attribute/metamechanic being used previously in the skilltree.  

|   Variable Placeholder                                                                                  |   Generated by                                                                                          |   Function                                                                                              |
|:-------------------------:|---------------------------------|------------------------------------------|
| <caster.var.{VariableName}>                                                                                |    | Returns the value of the variable {VariableName} on the variable registry of the caster of the mechanic                                                                                                   |
| <target.var.{VariableName}>                                                                                |    | Returns the value of the variable {VariableName} on the variable registry of the target of the mechanic                                                                                                   |
| <world.var.{VariableName}>                                                                                |    | Returns the value of the variable {VariableName} on the variable registry of the world the mechanic is used in                                                                                                   |
| <global.var.{VariableName}>                                                                                |    | Returns the value of the variable {VariableName} on the variable registry of the whole server                                                                                                   |
| <skill.var.{VariableName}>                                                                                    |    | Returns the value of the variable {VariableName} on the current [skill tree](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Skills/SkillTrees) |
| <skill.var.damage-amount>                                                                               | [~onDamaged] trigger <br> [~onAttack] trigger <br> [~onBowHit] trigger <br> [onDamaged] mechanic <br> [onAttack] mechanic                                                                                       | Returns the amount of damage taken or done                                                                      |
| <skill.var.damage-type>                                                                                 | [~onDamaged] trigger <br> [~onAttack] trigger <br> [~onBowHit] trigger <br> [onDamaged] mechanic <br> [onAttack] mechanic                                                                                                                     | Returns the type of damage taken or done, if any                                                                        |
| <skill.var.damage-cause>                                                                                 | [~onDamaged] trigger <br> [~onAttack] trigger <br> [~onBowHit] trigger <br> [onDamaged] mechanic <br> [onAttack] mechanic                                                                                                                  | Returns the cause of damage taken/done                                                                        |
| <skill.var.aura-name>                                                                                   | Every [aura] mechanic                                                                                   | Returns the name of the aura                                                                            |
| <skill.var.aura-type>                                                                                   | Every [aura] mechanic                                                                                   | Returns the type of the aura                                                                            |
| <skill.var.aura-charges>                                                                                | Every [aura] mechanic                                                                                   | Returns the amount of charges the aura has left                                                         |
| <skill.var.aura-duration>                                                                               | Every [aura] mechanic                                                                                   | Returns the remaining duration of the aura                                                              |
| <skill.var.aura-duration-millis>                                                                        | Every [aura] mechanic                                                                                   | Returns the remaining duration of the aura, in milliseconds                                             |
| <skill.var.aura-stacks>                                                                                 | Every [aura] mechanic                                                                                   | Returns the amount of stacks the aura has left                                                          |
| <skill.var.input>                                                                                       | [onChat] mechanic                                                                                       | Returns the chat input                                                                                  |
| <skill.targets>                                                                                         |    | Returns the amount of inherited targets                                                            |
| <skill.var.interval>                                                                                    | Using the `repeat` and `repeatInterval` [universal attributes]                                          | Returns the current iteration                                                                           |
| <skill.var.itr>                                                                                         | Using the `repeat` and `repeatInterval` [universal attributes]                                          | Returns the current iteration                                                                           |
| <skill.var.volume>                                                                                      | [~onHear] trigger                                                                                       | Returns a float value between 1 and 15 representing the intensity of the sound. Directly proportional to the distance (the further away the source, the higher this value)                                        |
| <skill.var.sound-type>                                                                                  | [~onHear] trigger                                                                                       | Returns the type of the sound                                                                           |
| <skill.var.hit-block-type>                                                                                  | [raytrace] mechanic                                                                                     | Returns the block that was hit, or AIR if none                                                          |
| <skill.var.bow-tension>                                                                                  | [~onShoot] trigger                                                                                      | Returns the force with which the projectile has been shot                                               |

```yaml
  Skills:
  - setvariable{var=caster.test1;val=1} @self
  - setvariable{var=target.test2;val=2} @self
  - message{m=<caster.var.test1> <caster.var.test2> <target.var.test1> <target.var.test2>} @self
```
> If you execute this metaskill yourself, this will send you a message saying `1 2 1 2` because the target of every mechanic is the caster, so the affected registry is always the caster's even if a "target" scope is used

### Meta Variable Placeholders

You can append some keywords (that we will call "meta keywords"), each specific to a variable's type, at the end of a variable placeholder in order to modify its return value and type.

```yaml
<{VariableScope}.var.{VariableName}.{keywords}>
```

Each keyword has an
- `Input Type`, which is the variable type the keyword applies to
- `Output Type`, which is the variable type that can be created from the keyword's returned value

> Placeholder support is allowed in every place inside of Variable Placeholders, so each keyword can also be another placeholder to be parsed

##

```yaml
<skill.var.exampleString.capitalize>
```
> Among all keywords for the String type, we are using the `capitalize` one, which has as an output a String type. This means that
> - It is applied to a String variable
> - It does some form of conversion to its value (in this case, capitalizing every character of the string)
> - It returns a String value


```yaml
<skill.var.exampleString.size>
```
> Among all keywords for the String type, we are using the `size` one, which has as an output an Integer type. This means that
> - It is applied to a String variable
> - It does some form of conversion to its value (in this case, returning the length of the string)
> - It returns an Integer value

## 

Given that each meta keyword has a specific input and output type, it is possible to *chain* them together, obtaining a compound effect where each keyword coverts the variable's value and pass the result to the following one

```yaml
<skill.var.exampleString.substring.0.9.size.add.1>
```
> Among all keywords for the String type, we are using the `substring` one, which has as an output a String type. This means that
> - It is applied to a String variable
> - It does some form of conversion to its value (in this case, extracting the first 10 characters from the string)
> - It returns a String value
>
> Among all keywords for the String type, we are using the `size` one, which has as an output an Integer type. This means that
> - It is applied to a String variable (which the `substring` keyword just returned)
> - It does some form of conversion to its value (In this case, returning the length of the string, which we know will be between 0 and 10)
> - It returns an Integer value
>
> Among all keywords for the Integer type, we are using the `add` one, which has as an output an Integer type. This means that
> - It is applied to an Integer variable (which the `size` keyword just returned)
> - It does some form of conversion to its value (In this case, adding a value of 1 to the integer's value)
> - It returns an Integer value

#### Universal Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .expires | BOOLEAN | Whether the variable can expire             |
| .expiration | TIME | The expiration timestamp for the variable   |
| .saved | BOOLEAN |Whether the variable is saved                  |
| .type | STRING | The type of the variable                        |
| .get | STRING | Forcefully returns the value of the variable. Used to make the "to{VariableType}" keyword return a correctly formatted value                             |
| .toint | INTEGER | Converts the value to an Integer without doing any specific operation, allowing chaining for Integer meta keywords. If not further keyword is used after this, the value will not be formatted as an Integer |
| .tofloat | FLOAT | Converts the value to a Float without doing any specific operation, allowing chaining for Float meta keywords. If not further keyword is used after this, the value will not be formatted as a Float |
| .todouble | DOUBLE | Converts the value to a Double without doing any specific operation, allowing chaining for Double meta keywords. If not further keyword is used after this, the value will not be formatted as a Double |
| .toboolean | BOOLEAN | Converts the value to a Boolean without doing any specific operation, allowing chaining for Boolean meta keywords. If not further keyword is used after this, the value will not be formatted as a Boolean |
| .tostring | STRING | Converts the value to a String without doing any specific operation, allowing chaining for String meta keywords. If not further keyword is used after this, the value will not be formatted as a String |
| .tolocation | LOCATION | Converts the value to a Location without doing any specific operation, allowing chaining for Location meta keywords. If not further keyword is used after this, the value will not be formatted as a Location |
| .tovector | VECTOR | Converts the value to a Vector without doing any specific operation, allowing chaining for Vector meta keywords. If not further keyword is used after this, the value will not be formatted as a Vector |
| .tolist | LIST | Converts the value to a List without doing any specific operation, allowing chaining for List meta keywords. If not further keyword is used after this, the value will not be formatted as a List |
| .toset | SET | Converts the value to a Set without doing any specific operation, allowing chaining for Set meta keywords. If not further keyword is used after this, the value will not be formatted as a Set |
| .tomap | MAP | Converts the value to a Map without doing any specific operation, allowing chaining for Map meta keywords. If not further keyword is used after this, the value will not be formatted as a Map |
| .totime | TIME | Converts the value to a Time without doing any specific operation, allowing chaining for Time meta keywords. If not further keyword is used after this, the value will not be formatted as a Time |

#### Integer Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add.{Integer} | INTEGER | The addition between the value and the specified Integer |
| .sub.{Integer} | INTEGER | The subtraction between the value and the specified Integer |
| .mul.{Integer} | INTEGER | The multiplication between the value and the specified Integer |
| .div.{Integer} | INTEGER | The division between the value and the specified Integer |
| .abs | INTEGER | The absolute value of the value |

#### Float Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add.{Float} | FLOAT | The addition between the value and the specified Float |
| .sub.{Float} | FLOAT | The subtraction between the value and the specified Float |
| .mul.{Float} | FLOAT | The multiplication between the value and the specified Float |
| .div.{Float} | FLOAT | The division between the value and the specified Float |
| .abs | FLOAT | The absolute value of the value |

#### Double Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .add.{Double} | DOUBLE | The addition between the value and the specified Double |
| .sub.{Double} | DOUBLE | The subtraction between the value and the specified Double |
| .mul.{Double} | DOUBLE | The multiplication between the value and the specified Double |
| .div.{Double} | DOUBLE | The division between the value and the specified Double |
| .abs | DOUBLE | The absolute value of the value |

#### Boolean Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|----------|
| .inverse     | BOOLEAN     | The inverse of the value |
| .number      | INTEGER     | The value as either a 0 (false) or 1 (true) |
| .yesno       | STRING      | The value as either a no (false) or yes (true) |
| .union.{Boolean} | BOOLEAN | Logical OR with specified Boolean |
| .intersection.{Boolean} | BOOLEAN | Logical AND with specified Boolean |
| .difference.{Boolean} | BOOLEAN | True if value is true and argument is false |

#### String Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | The length of the string |
| .uppercase | STRING | The string in uppercase |
| .lowercase | STRING | The string in lowercase |
| .capitalize | STRING | The string with the first character in uppercase |
| .trim | STRING | The string with leading and trailing spaces removed |
| .replace.{old}.{new} | STRING | The string with occurrences of `old` replaced by `new` |
| .remove.{text} | STRING | The string with occurrences of `text` removed |
| .contains.{text} | BOOLEAN | Whether the string contains `text` |
| .substring.{start}.{end} | STRING | A substring from index `start` to `end` |
| .split.{regex}.{joiner} | STRING | Splits the string by `regex`, then joins it with `joiner` |
| .indexof.{text} | INTEGER | The index of the first occurrence of `text` |
| .lastindexof.{text} | INTEGER | The index of the last occurrence of `text` |
| .startswith.{text} | BOOLEAN | Whether the string starts with `text` |
| .endswith.{text} | BOOLEAN | Whether the string ends with `text` |
| .append.{text} | STRING | Appends `text` to the end of the string |
| .prepend.{text} | STRING | Prepends `text` to the beginning of the string |
| .insert.{index}.{text} | STRING | Inserts `text` at the specified `index` |
| .regex.{pattern} | BOOLEAN | Whether the string matches the regex `pattern` |
| .{index} | STRING | Returns the character at the specified `index` |

#### Set Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | The number of elements in the set |
| .join.{delimiter} | STRING | Joins all elements using the `delimiter` |
| .contains.{element} | BOOLEAN | Whether the set contains the given `element` |

#### Location Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .x | DOUBLE | The X coordinate |
| .y | DOUBLE | The Y coordinate |
| .z | DOUBLE | The Z coordinate |
| .world | STRING | The world name |
| .yaw | DOUBLE | The yaw |
| .pitch | DOUBLE | The pitch |
| .coords | LIST | A list with the X, Y, and Z coordinates |

#### Vector Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .x | DOUBLE | The X component |
| .y | DOUBLE | The Y component |
| .z | DOUBLE | The Z component |
| .normalized | VECTOR | The normalized vector |
| .length | DOUBLE | The length (magnitude) of the vector |
| .mul.{vector} | VECTOR | Multiplies the vector by another vector |
| .div.{vector} | VECTOR | Divides the vector by another vector |
| .add.{vector} | VECTOR | Adds another vector |
| .sub.{vector} | VECTOR | Subtracts another vector |
| .rotate.{axis}.{angle} | VECTOR | Rotates the vector around `axis` by `angle` radians |

#### List Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | Number of elements in the list |
| .first | STRING | First element in the list |
| .last | STRING | Last element in the list |
| .reverse | LIST | The list reversed |
| .sort | LIST | The list sorted alphabetically |
| .pop | STRING | Removes and returns the last element. Does side effect on the list |
| .shift | STRING | Removes and returns the first element. Does side effect on the list |
| .get.{index} | STRING | Element at specified `index` |
| .join.{delimiter} | STRING | Joins elements using `delimiter` |
| .contains.{element} | BOOLEAN | Whether the list contains `element` |
| .maxnumber | DOUBLE | Maximum numerical value in list |
| .minnumber | DOUBLE | Minimum numerical value in list |
| .indexof.{value} | INTEGER | Index of first occurrence of `value` |
| .lastindexof.{value} | INTEGER | Index of last occurrence of `value` |
| .slice.{from}.{to} | LIST | Slice of list from `from` to `to` |
| .slicefrom.{index} | LIST | Slice of list from `index` to end |
| .sliceto.{index} | LIST | Slice of list from start to `index` |
| .append.{value} | LIST | Adds `value` to the end of the list |
| .prepend.{value} | LIST | Adds `value` to the start of the list |
| .insert.{index}.{value} | LIST | Inserts `value` at the given `index` |
| .remove.{index} | LIST | Removes value at given `index` |
| .{index} | STRING | Element at specified `index` |

#### Map Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .size | INTEGER | Number of key-value pairs |
| .keys | LIST | List of all keys |
| .values | LIST | List of all values |
| .get.{key} | STRING | Value associated with the specified `key` |
| .{key} | STRING | Value associated with the specified `key` |

#### Time Meta Keywords
|  Placeholder | Return Type | Return Value |
|--------------|-------------|--------------|
| .delta.{timestamp} | INTEGER | Difference between the value's time and the and given `timestamp` |
| .formatted.{pattern} | STRING | Formatted date/time using the specified pattern. The pattern can be anything the Java function [ZoneOffset.of](https://docs.oracle.com/javase/8/docs/api/java/time/ZoneOffset.html#of-java.lang.String-) accepts |
| .duration | STRING | Interprets the Time as a raw "amount of milliseconds" and displays the total amount of Seconds, Minutes, Hours, Days, Months and Years. Can be useful for countdowns and the likes, especially if paired with the `.delta` meta keywords|

# Placeholder Attributes
Some placeholders can use a set of attributes to further define the output they will give

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| rounding  | round, r  | The rounding of the returned float value                             | 2       |

```yaml
  Skills:
  - message{m="<target.hp{round=2}>"} @self
```


# PlaceholderAPI Integration
Other than being able to use PlaceholderAPI placeholders anywhere placeholder support is in place, MythicMobs introduces some new PAPI placeholders that can be used by third parties to fetch MythicMobs-related values.
| **PAPI Placeholder**        | **Function**                                                            |
|-----------------------------|-------------------------------------------------------------------------|
| %mythic_var_someVar%        | Returns the value of the `someVar` variable that is set on the player   |
| %mythic_var_world_someVar%  | Returns the value of the `someVar` variable that is set on the world    |
| %mythic_var_global_someVar% | Returns the value of the `someVar` variable that is set on the server   |
| %mythic_var_\<playerName\>_someVar% | Returns the value of the `someVar` variable that is set on the specified player, by their name |
| %mythic_var_\<UUID\>_someVar% | Returns the value of the `someVar` variable that is set on the specified entity, by its UUID|
| %mythic_spawner_[name]_cooldown% | Returns the cooldown of the spawner called `name`                  |
| %mythic_spawner_[name]_cooldownleft% | Returns the remaining cooldown of the spawner called `name`    |
| %mythic_spawner_[name]_warmup% | Returns the warmup of the spawner called `name`                      |
| %mythic_spawner_[name]_warmupleft% | Returns the remaining warmup of the spawner called `name`        |
| %mythic_stat_[name]%        | Returns the value of the specified stat on the evaluated player         |

## PlaceholderAPI Parsing
When using placeholders via PlaceholderAPI, it is important to remember that some of them are meant to be parsed against a player, and if parsed against a mob they may behave unexpectedly.  
More concretely, this means that:  
- If used inside a mechanic, the target must be a player  
- If used inside a condition, the checked entity must be a player (caster for conditions, inherited targets for targetconditions, trigger for triggerconditions)  

...and so on  

# Custom Placeholders
It's possible to create custom placeholders in any Pack by creating a file named `placeholders.yml` in the pack directory. These can be static or you can define conditional placeholders - the first one that evaluates true will be chosen, or the `Default` if they're all false.

Custom placeholders can be used via `<placeholder.[CustomPlaceholder]>`, with _[CustomPlaceholder]_ being the name of your custom placeholder.  

```yaml
TestPlaceholder: 'some value'

TestConditionalPlaceholder:
  Day:
    Conditions:
    - day
    Value: day
  Night:
    Conditions:
    - night
    Value: night
  Default: idk

TestRandomPlaceholder:
- red
- green
- blue
```
> A value of "null" is not accepted


# Examples
**This will make a mob send a teal message to all players in a radius of 20 blocks around in itself, stating what entity killed it in green.**

```yaml
    Skills:
    - message{m="<&b><caster.name><&r> was slain by <&a><trigger.name><&r>."} @PIR{r=20} ~onDeath
```

**This skill will make an announcement when the mob spawns that looks like this:**

![image](uploads/91ed6d8aaa669e8ae21f8745e8ff4643/image.png)

```yaml
  Skills:
  - Skill{s=SaveBossLocation} @self ~onSpawn
  - message{m="&eA &BGiant Zombie&e (Level &4<caster.level>&e) &ehas spawned at <caster.var.SpawnLoc>"} ~onSpawn @PlayersInWorld
  - message{m="&eThe &BGiant Zombie&e (Level &4<caster.level>&e) &espawned at <caster.var.SpawnLoc>&e has been slain."} ~onDeath @PlayersInWorld
```

Be sure to place this skill somewhere in the skills file

```yaml
SaveBossLocation:
  Skills:
  - setvariable{var=SpawnLoc;type=STRING;value="&b<caster.l.x>&e, &b<caster.l.y>&e, &b<caster.l.z>";scope=CASTER} @self
```
**You can also use color tags and formatting tags to make the mobs have pretty names:**

![image](uploads/9ad97422803c3f35fbeac2e4df7f7d52/image.png)

```yaml
ZOMBIE:
  Display: 'ZOMBIE &F- &A<caster.hp>/<caster.mhp>HP &F- &ELv.<caster.level>'
```


<!-- LINKS -->
[~onHear]: /Skills/Triggers/onHear
[~onDamaged]: /Skills/Triggers/onDamaged
[~onAttack]: /Skills/Triggers/onAttack
[~onBowHit]: /Skills/Triggers/onBowHit
[~onShoot]: /Skills/Triggers/onShoot
[onChat]: /skills/mechanics/onChat
[aura]: /skills/mechanics/aura
[raytrace]: /skills/mechanics/raytrace
[raytraceto]: /skills/mechanics/raytraceto
[onDamaged]: /skills/mechanics/onDamaged
[onAttack]: /skills/mechanics/onAttack
[universal attributes]: /Skills/Mechanics#universal-attributes
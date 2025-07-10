# Introduction

Stats are values that affect all kinds of mechanics across Players, Mobs, Items, Skills, and more.
While Stats system can be complicated to learn at first, its versatility will enable you to do very advanced things, such as combat changes, technical utilities, and the creation of new game design elements.  

Stats are defined in the`stats.yml` file. This file can exist in the root directory of MythicMobs (`/plugins/MythicMobs/`) or in a [Pack](MythicMobs/-/wikis/Packs) folder.

> **WARNING: To be able to use Stats on Items, [Crucible](/../../../mythiccrucible/-/wikis/home) must be installed**

- [Custom Stat Options](#custom-stat-options)
  - [Custom Stat Types](#custom-stat-types)
  - [Specific Type Options](#specific-type-options)
  - [Tooltips Formatting](#tooltips-formatting)
- [Modifiers](#modifiers)
- [Built In Stats](#built-in-stats)
- [Implementations with Configurations](#implementations-with-configurations)
  - [Mobs](#mobs)
  - [Items](#items)
- [Examples](#Examples)
  - [Example Custom Stats](#example-custom-stats)


# Custom Stat Options
Options that can be used in the Stat in order to better customize it

| Option               |Description                                                                      |
|----------------------|---------------------------------------------------------------------------------|
| Enabled              | If the stat is currently enabled                                                |
| AlwaysActive         | If the stat is forcefully applied to every registry of every entity             |
| Type                 | The [Type](Stats#custom-stat-types) of the stat                                 |
| Display              | The name with which the stat is displayed                                       |
| Formatting           | How the stat is shown on items. Depends on the Modifier used                    |
| ShowInLore           | Whether to show the tooltips formatting for each modifier                       |
| Priority             | The priority with which the stat will take effect, compared to others. *Lower* values make it so the stat will trigger *before* stats with higher values |
| MinValue             | Minimum value for the stat                                                      |
| MaxValue             | Max value for the stat                                                          |
| Triggers             | What triggers the stat effect. Can be any MythicMobs trigger, minus the "on" bit. <br />(For instance: to use `onAttack`, one needs to write `ATTACK` as a trigger) <br />As of v.5.4.0, only damaging triggers are available; keep an eye on dev builds for expanded functionality.|
| ParentStats          | A list of other stats that this stat relies on                                  |
| TriggerStats         | A list of stats that the triggering entity may have and their FormulaKey, separated by a space. The FormulaKey can then be used in other Formulas to fetch its value from the trigger's. [Here is an example](#ice_damage) |
| Formula              | A formula for the base value if this stat has parent stats                      |
| FormulaKey           | A key you can use in formulas, when this stat is the parent of another          |
| BaseValue            | A static base value if it doesn't have parents                                  |
| ExecutionPoint       | For stats that modify a trigger, can be `PRE` or `POST`. determines whether the stat is evaluated before or after any mechanics |
| Skills               | The skills that get executed when the stat is activated                         |

## Custom Stat Types
The values that the `Type` Option can be set to
| Type                 |Description                                                                      |
|----------------------|---------------------------------------------------------------------------------|
| `STATIC`             | A static value. Does nothing on its own, but can be referenced via placeholders |
| `DAMAGE_BONUS`       | This stat adds a flat amount of bonus damage                                    |
| `DAMAGE_MODIFIER`    | Modifies the damage using a formula                                             |
| `PROC`               | A chance to execute skills                                                      | 

## Specific Type Options
A list of options only available if the specified type is used in the stat

### DAMAGE_MODIFIER

| Option               |Description                                                                      |
|----------------------|---------------------------------------------------------------------------------|
| DamageType           | Specify a custom damage type. Use `ALL` to modify the final total damage of the skill                  |
| Conditions           | Specify conditions which can affect the Modifier                                |
| DamageFormula        | Define a formula for how the damage is modified. See [HERE](#fire_resistance) for an example of this<br>Some additional keys the damage formula can use are:<br>- `d` to express the damage's original value<br>- `v` to express the stat's value |

### DAMAGE_BONUS

| Option               |Description                                                                      |
|----------------------|---------------------------------------------------------------------------------|
| DamageType           | Specify a custom damage type                                                    |


## Tooltips Formatting
| Formatting           |Description                                                                      |
|----------------------|---------------------------------------------------------------------------------|
| Additive             | The tooltip to show for additive modifiers                                      |
| Multiply             | The tooltip to show for multiply modifiers                                      |
| Compound             | The tooltip to show for compound modifiers                                      |
| Setter               | The tooltip to show for setter modifiers                                        |
| Rounding             | The amount of numbers after the point in the value of the stat                  |
| ShowInItemLore       | Whether the tooltips should be shown in an items's lore whenever `{stats-each}` is used. Defaults to true, overridden by the ShowInLore options if they are set |

| ShowInLore           | Description                                                                     |
|----------------------|---------------------------------------------------------------------------------|
| Additive             | Whether to show the Additive modifier tooltip in an item's lore                 |
| Multiply             | Whether to show the Multiply modifier tooltip in an item's lore                 |
| Compound             | Whether to show the Compound modifier tooltip in an item's lore                 |
| Setter               | Whether to show the Setter modifier tooltip in an item's lore                   |

```yml
EXAMPLE_STAT:
  Enabled: true
  AlwaysActive: false
  Type: STATIC
  FormulaKey: 'SPD'
  Formatting:
    Additive: '+<value> Speed'
    Multiply: '+<value>% Speed'
    Compound: 'x<value>% Speed'
    Static: 'Force <value> <display>'
    Rounding: 2
  ShowInLore:
    Compound: false # optional
```

# Modifiers
Modifiers can be used to adjust stats after their base value is defined.
| Modifier             |Description                                                                                        |
|----------------------|---------------------------------------------------------------------------------------------------|
| `ADDITIVE`           | Adds to the base value of a stat                                                                  |
| `ADDITIVE_MULTIPLIER`| Adds a multiplier the base value of a stat                                                        |
| `COMPOUND_MULTIPLIER`| Multiplies the base value of a stat, then adds it to the base value                               |
| `SETTER`             | Overrides all modifiers and base values, and forces the stat to be what is defined                |

Note that stat modifiers can be applied to and by mobs, players, items, enchants, and auras. For example, an item may add to or multiply its wielder's attack speed, while an attack may temporarily apply a COMPOUND MULTIPLIER to half a target's attack speed.

<!--
TODO: define mechanics that can manipulate modifiers
-->

##

#### `ADDITIVE`
The `ADDITIVE` modifiers are straightforward: they add to the base stat.
#### `ADDITIVE_MULTIPLIER`
The `ADDITIVE_MULTIPLIER` multiply the value of the base stat by the specified value.  
They all pool together (i.e. additive multipliers of 2 and 3 becoming a multiplier of 5, NOT 6) to then multiply the base stat after additives.
#### `COMPOUND_MULTIPLIER`
Finally, the `COMPOUND_MULTIPLIER` multiplies all the ADDITIVE results afterwards - this is a great place for to apply effect changes such as debuffs, since they would typically be calculated after additive stat additions and multipliers.

##

## Stat Calculation 
The two `ADDITIVE_MULTIPLIER` and `COMPOUND_MULTIPLIER` modifiers can be easy to mix up; however, this example should make it a bit more clear:

Lets say you have these modifiers:
 ``` rb
  8 base value
  10 additive
  2 additive
  5 multiply
  3 multiply
  2 compound   (effectively x2)
  0.4 compound (effectively -60%)
```
...the resulting math MythicMobs would calculate this is as follows:
```rb
(8 + 10 + 2) * (5 + 3) * (2 * 0.4) = 128

(base + additive + additive) * (additive_multiplier + additive_multiplier) * (compound_multiplier * compound_multiplier) = final stat
```
Regular multipliers are additive, and compound multipliers are multiplicative. You can think of it as "+10%" for Additive Multipliers  vs. "x10%" for Compound Multipliers.


# Built-In Stats

These stats are inherently supported by MythicMobs, and can be configured in the `stats.yml` file in the plugin's root directory (`/plugins/MythicMobs/`) or inside Pack folders. (`/plugins/MythicMobs/Packs/CoolPack/`)
The player inherits the `BaseValue` of these stats; Mobs also inherit them as defaults, unless overrides are specified in the `Stats:` sub-section of their config.


|Stat                                                         |Description                                                                                       |
|-------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
|[ATTACK_DAMAGE](#attack_damage)                              |Base Damage Output                                                                                |
|[ATTACK_SPEED](#attack_speed)                                |Attack cooldown frequency. Typically only used for Players.                                       |
|[BONUS_DAMAGE](#bonus_damage)                                |Additional Modifier for dealing extra damage                                                      |
|[CRITICAL_STRIKE_CHANCE](#critical_strike_chance)            |Chance to land a Critical Strike (Chance-based Crit)                                              |
|[CRITICAL_STRIKE_DAMAGE](#critical_strike_damage)            |Damage dealt via Critical Strike                                                                  |
|[CRITICAL_STRIKE_RESILIENCE](#critical_strike_resilience)    |Resistance to Critical Strike                                                                     |
|[DAMAGE_REDUCTION](#damage_reduction)                        |Generic damage reduction                                                                          |
|[DEFENSE](#defense)                                          |Defense                                                                                           |
|[DODGE_CHANCE](#dodge_chance)                                |Chance for an attack to fail when attempting to damage. Reduced by opponent's [DODGE_NEGATION](#dodge_negation). |
|[DODGE_NEGATION](#dodge_negation)                                        |Reduces opponent's [DODGE_CHANCE](#dodge_chance).            |
|[HEALTH](#health)                                            |Health values                                                                                     |
|[HEALTH_REGENERATION](#health_regeneration)                  |Rate of Health Regeneration                                                                       |
|[LIFESTEAL_CHANCE](#lifesteal_chance)                        |Chance for damage dealt to heal the attacker                                                      |
|[LIFESTEAL_POWER](#lifesteal_power)                          |How much healing LifeSteal does.                                                                  |
|[MOVEMENT_SPEED](#movement_speed)                            |Movement Speed.                                                                                   |
|[PARRY_CHANCE](#parry_chance)                                |Chance to mitigate and reflect damage from sources that melee you from the front. Reduced by opponent's [PARRY_NEGATION](#parry_negation). |
|[PARRY_COUNTERATTACK](#parry_counterattack)                  |How much damage is returned to the opponent when parrying.                                        |
|[PARRY_POWER](#parry_power)                                  |How much damage is mitigated by Parry.                                                            |
|[PARRY_NEGATION](#parry_negation)                                      |Reduces the [PARRY_CHANCE](#parry_chance) of the opponent. |
| [SCALE](#scale)                                             | The scale of the entity                |
| STEP_HEIGHT                                                 | The step height attribute                |
| ARMOR                                                       | The armor attribute                      |
| ARMOR_TOUGHNESS                                             | The armor toughness attribute            |
| BURNING_TIME                                                | The burning time attribute               |
| EXPLOSION_KNOCKBACK_RESISTANCE                          | The explosion knockback resistance attribute |
| FALL_DAMAGE_MULTIPLIER                                      | The fall damage multiplier attribute     |
| GRAVITY                                                     | The gravity attribute                    |
| JUMP_STRENGTH                                               | The jump strength attribute              |
| KNOCKBACK_RESISTANCE                                        | The knockback resistance attribute       |
| MOVEMENT_EFFICIENCY                                         | The movement efficiency attribute        |
| OXYGEN_BONUS                                                | The oxygen bonus attribute               |
| SAFE_FALL_DISTANCE                                          | The safe fall distance attribute         |
| SNEAKING_SPEED                                              | The sneaking speed attribute             |
| WATER_MOVEMENT_EFFICIENCY                                   | The water movement efficiency attribute  |
| BLOCK_BREAK_SPEED                                           | The block break speed attribute          |
| BLOCK_INTERACTION_RANGE                                     | The block interaction range attribute    |
| ENTITY_INTERACTION_RANGE                                    | The entity interaction range attribute   |
| FLYING_SPEED                                                | The flying speed of the entity           |
| FOLLOW_RANGE                                                | The follow range of the entity           |

# Built-in Stats Breakdown

This is a detailed breakdown of the built-in stats provided by MythicMobs. For custom stats, see [Custom Stat Examples](#example-custom-stats).

#### `DODGE_NEGATION`
Chance for an attack to land damage. Reduces opponent's [DODGE_CHANCE](#dodge_chance).
As shown below, the displayed name and lore elements of a stat can be customized, such as 'Accuracy' instead of 'Dodge Negation'

<details><summary>Configuration</summary>
<br>

```yml
DODGE_NEGATION:
  Enabled: false
  AlwaysActive: false
  Display: 'Accuracy'
  Formatting:
    Additive: '+<value> Accuracy'
    Multiply: '+<value> Accuracy'
    Compound: 'x<value> Accuracy'
  BaseValue: 0
```

</details>

##
#### `ATTACK_DAMAGE`
Base Damage Output
<details><summary>Configuration</summary>
<br>

```yml
ATTACK_DAMAGE:
  Enabled: true
  AlwaysActive: false
  Display: 'Damage'
  Formatting:
    Additive: '+<value> Damage'
    Multiply: '+<value> Damage'
    Compound: 'x<value> Damage'
  BaseValue: 1
```

</details>

##
#### `ATTACK_SPEED`
Attack cooldown frequency. Typically only used for Players.
<details><summary>Configuration</summary>
<br>

```yml
ATTACK_SPEED:
  Enabled: true
  AlwaysActive: false
  Display: 'Attack Speed'
  Formatting:
    Additive: '+<value> Attack Speed'
    Multiply: '+<value> Attack Speed'
    Compound: 'x<value> Attack Speed'
  BaseValue: 4.0
```

</details>

##
#### `BONUS_DAMAGE`
Additional Modifier for dealing extra damage
<details><summary>Configuration</summary>
<br>

```yml
BONUS_DAMAGE:
  Enabled: false
  AlwaysActive: false
  Display: 'Bonus Damage'
  Formatting:
    Additive: '+<value> Bonus Damage'
    Multiply: '+<value> Bonus Damage'
    Compound: 'x<value> Bonus Damage'
  BaseValue: 0
```

</details>

##
#### `CRITICAL_STRIKE_CHANCE`
Chance to land a Critical Strike (Chance-based Crit)
<details><summary>Configuration</summary>
<br>

```yml
CRITICAL_STRIKE_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Critical Strike'
  Formatting:
    Additive: '+<value> Critical Strike'
    Multiply: '+<value> Critical Strike'
    Compound: 'x<value> Critical Strike'
  BaseValue: 0
  MinValue: 0
  Skills:
  - particles{p=crit;a=50;hS=1;y=1;s=1} @trigger
```

</details>

##
#### `CRITICAL_STRIKE_DAMAGE`
Damage dealt via Critical Strike
<details><summary>Configuration</summary>
<br>

```yml
CRITICAL_STRIKE_DAMAGE:
  Enabled: false
  AlwaysActive: true
  Display: 'Critical Damage'
  Formatting:
    Additive: '+<value> Critical Damage'
    Multiply: '+<value> Critical Damage'
    Compound: 'x<value> Critical Damage'
  BaseValue: 1
```

</details>

##
#### `CRITICAL_STRIKE_RESILIENCE`
Resistance to Critical Strike
<details><summary>Configuration</summary>
<br>

```yml
CRITICAL_STRIKE_RESILIENCE:
  Enabled: false
  Display: 'Resilience'
  AlwaysActive: false
  Formatting:
    Additive: '+<value> Resilience'
    Multiply: '+<value> Resilience'
    Compound: 'x<value> Resilience'
  BaseValue: 0
```

</details>

##
#### `DAMAGE_REDUCTION`
Generic damage reduction
<details><summary>Configuration</summary>
<br>

```yml
DAMAGE_REDUCTION:
  Enabled: false
  AlwaysActive: false
  Display: 'Damage Reduction'
  Formatting:
    Additive: '+<value> Damage Reduction'
    Multiply: '+<value> Damage Reduction'
    Compound: 'x<value> Damage Reduction'
  BaseValue: 0
```

</details>

##
#### `DEFENSE`
Defense
<details><summary>Configuration</summary>
<br>

```yml
DEFENSE:
  Enabled: false
  AlwaysActive: false
  Display: 'Defense'
  Formatting:
    Additive: '+<value> Defense'
    Multiply: '+<value> Defense'
    Compound: 'x<value> Defense'
  BaseValue: 0
```

</details>

##
 #### `DODGE_CHANCE`
 Chance for an attack to fail when attempting to damage. Reduces opponent's [ACCURACY](#accuracy).
<details><summary>Configuration</summary>
<br>

```yml
DODGE_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Dodge'
  Formatting:
    Additive: '+<value> Dodge Chance'
    Multiply: '+<value> Dodge Chance'
    Compound: 'x<value> Dodge Chance'
  BaseValue: 0
  Skills: []
```

</details>

##
#### `HEALTH`
Health values
<details><summary>Configuration</summary>
<br>

```yml
HEALTH:
  Enabled: false
  AlwaysActive: true
  Display: 'Health'
  Formatting:
    Additive: '+<value> Health'
    Multiply: '+<value> Health'
    Compound: 'x<value> Health'
  BaseValue: 20
  MinValue: 1
```

</details>

##
#### `HEALTH_REGENERATION`
Rate of Health Regeneration
<details><summary>Configuration</summary>
<br>

```yml
HEALTH_REGENERATION:
  Enabled: false
  AlwaysActive: false
  Display: 'Health Regeneration'
  Formatting:
    Additive: '+<value> Regeneration'
    Multiply: '+<value> Regeneration'
    Compound: 'x<value> Regeneration'
  BaseValue: 0
  MaxValue: 1000000
  MinValue: 0
  Frequency: 60
```

</details>

##
#### `LIFESTEAL_CHANCE`
Chance for damage dealt to heal the attacker
<details><summary>Configuration</summary>
<br>

```yml
LIFESTEAL_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Lifesteal Chance'
  Formatting:
    Additive: '+<value> Lifesteal Chance'
    Multiply: '+<value> Lifesteal Chance'
    Compound: 'x<value> Lifesteal Chance'
  BaseValue: 0
```

</details>

##
#### `LIFESTEAL_POWER`
How much healing LifeSteal does.
<details><summary>Configuration</summary>
<br>

```yml
LIFESTEAL_POWER:
  Enabled: true
  AlwaysActive: false
  Display: 'Lifesteal Power'
  Formatting:
    Additive: '+<value> Lifesteal Power'
    Multiply: '+<value> Lifesteal Power'
    Compound: 'x<value> Lifesteal Power'
  BaseValue: 0.1
```

</details>

##
#### `MOVEMENT_SPEED`
Movement Speed.
<details><summary>Configuration</summary>
<br>

```yml
MOVEMENT_SPEED:
  Enabled: false
  AlwaysActive: true
  Display: 'Movement Speed'
  Formatting:
    Additive: '+<value> Movement Speed'
    Multiply: '+<value>% Movement Speed'
    Compound: 'x<value>% Movement Speed'
  ParentStats:
  - SPEED
  Formula: '0.2 + (0.2 / (1 + e^(-0.005 * (SPD - 1000))))'
```

</details>

##
#### `PARRY_CHANCE`
Chance to mitigate and reflect damage from sources that melee you from the front.
<details><summary>Configuration</summary>
<br>

```yml
PARRY_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Parry Chance'
  BaseValue: 0
  Priority: 0
  Formatting:
    Additive: '+<value> Parry Chance'
    Multiply: '+<value> Parry Chance'
    Compound: 'x<value> Parry Chance'
  FrontAngle: 180
  UsableMaterials:
    - WOODEN_SWORD
    - STONE_SWORD
    - GOLDEN_SWORD
    - IRON_SWORD
    - DIAMOND_SWORD
    - NETHERITE_SWORD
  Skills: []
```

</details>

##
#### `PARRY_COUNTERATTACK`
How much damage is returned to the opponent when parrying.
<details><summary>Configuration</summary>
<br>

```yml
PARRY_COUNTERATTACK:
  Enabled: false
  AlwaysActive: false
  Display: 'Parry Counterattack'
  BaseValue: 1
  Formatting:
    Additive: '+<value> Parry Counterattack'
    Multiply: '+<value> Parry Counterattack'
    Compound: 'x<value> Parry Counterattack'
```

</details>

##
#### `PARRY_NEGATION`
Affects and lowers the [PARRY_CHANCE](#parry_chance) of the opponent.
As shown below, the displayed name and lore elements of a stat can be customized, such as 'Expertise' instead of 'Parry Negation'
<details><summary>Configuration</summary>
<br>

```yml
PARRY_NEGATION:
  Enabled: false
  AlwaysActive: false
  Display: 'Expertise'
  Formatting:
    Additive: '+<value> Expertise'
    Multiply: '+<value> Expertise'
    Compound: 'x<value> Expertise'
  BaseValue: 0
```

</details>

##
#### `PARRY_POWER`
How much damage is mitigated by Parry.
<details><summary>Configuration</summary>
<br>

```yml
PARRY_POWER:
  Enabled: false
  AlwaysActive: false
  Display: 'Parry Power'
  BaseValue: 0.5
  Formatting:
    Additive: '+<value> Parry Power'
    Multiply: '+<value> Parry Power'
    Compound: 'x<value> Parry Power'
```

</details>

##
#### `SCALE`
The Scale of the entity
<details><summary>Configuration</summary>
<br>

```yml
SCALE:
  Enabled: false
  AlwaysActive: false
  Display: 'Scale'
  BaseValue: 1
  Formatting:
    Additive: '+<value> Scale'
    Multiply: '+<value> Scale'
    Compound: 'x<value> Scale'
```

</details>


##
# Implementations with Configurations

It's important to be aware that players get all of their base stat values from the `stats.yml` file, while mobs get only some of their base values from the `stats.yml` file: if another value is specified as one of their stats, that is applied.

## Mobs
This example features `Some_Mob` and three configured stats: `CRITICAL_STRIKE_CHANCE` as configured in the `Stats:` section, but also its `Health` and `Damage`.
The Health and Damage stat types are natively handled in the typical format of a mob's configuration. Other stats that are configured on the mob are: `ATTACK_DAMAGE`, `ATTACK_SPEED`, and `MOVEMENT_SPEED`.
```yml
Some_Mob:
  Health: 50
  Damage: 10
  Stats:
  - CRITICAL_STRIKE_CHANCE 0.2
```

## Items
```yaml
ExampleItem:
  Id: BLAZE_ROD
  Display: 'Test'
  Stats:
  - CRITICAL_STRIKE_CHANCE 0.5 ADDITIVE
  - CRITICAL_STRIKE_DAMAGE 2.0 ADDITIVE
  - HEALTH 20to30 ADDITIVE
```
> **WARNING: To be able to use Stats on Items, [Crucible](/../../../mythiccrucible/-/wikis/home) must be installed**

# Examples

## Example Custom Stats

These stats are created by the end user. Included are some examples.


#### `ARMOR_GENERIC`
Generic Armor based damage reduction. can be applied to gear.
```yml
ARMOR_GENERIC:
  Enabled: false
  AlwaysActive: false
  Type: DAMAGE_MODIFIER
  Triggers:
    - DAMAGED
  ExecutionPoint: PRE
  Display: 'Generic Armor'
  DamageFormula: 'd - v'
  BaseValue: 0
  Formatting:
    Additive: '+<value> Generic Armor'
    Multiply: '+<value> Generic Armor'
    Compound: 'x<value> Generic Armor'

```
#### `ARMOR_BLUNT`
Armor based damage reduction based on the `BLUNT` [DamageType.](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/damagetag)
```yml
ARMOR_BLUNT:
  Enabled: false
  AlwaysActive: false
  Type: DAMAGE_MODIFIER
  Triggers:
    - DAMAGED
  ExecutionPoint: PRE
  Display: 'Blunt Armor'
  DamageType: BLUNT
  DamageFormula: 'd - v'
  BaseValue: 0
  Formatting:
    Additive: '+<value> Blunt Armor'
    Multiply: '+<value> Blunt Armor'
    Compound: 'x<value> Blunt Armor'

```
#### `ARMOR_SHARP`
Armor based damage reduction based on the `SHARP` [DamageType.](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/damagetag)
```yml
ARMOR_SHARP:
  Enabled: false
  AlwaysActive: false
  Type: DAMAGE_MODIFIER
  Triggers:
    - DAMAGED
  ExecutionPoint: PRE
  Display: 'Sharp Armor'
  DamageType: SHARP
  DamageFormula: 'd - v'
  BaseValue: 0
  Formatting:
    Additive: '+<value> Sharp Armor'
    Multiply: '+<value> Sharp Armor'
    Compound: 'x<value> Sharp Armor'

```
#### `DAMAGE_BLUNT`
Damage Output for the `BLUNT` [DamageType.](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/damagetag)
```yml
DAMAGE_BLUNT:
  Enabled: false
  AlwaysActive: false
  Type: DAMAGE_BONUS
  Priority: 1
  Triggers:
    - ATTACK
  ExecutionPoint: PRE
  Display: 'Blunt Damage'
  DamageType: BLUNT
  BaseValue: 0
  Formatting:
    Additive: '+<value> Blunt Damage'
    Multiply: '+<value> Blunt Damage'
    Compound: 'x<value> Blunt Damage'

```
#### `DAMAGE_SHARP`
Damage Output for the `SHARP` [DamageType.](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/damagetag)

```yml
DAMAGE_SHARP:
  Enabled: false
  AlwaysActive: false
  Type: DAMAGE_BONUS
  Priority: 2
  Triggers:
    - ATTACK
  ExecutionPoint: PRE
  Display: 'Sharp Damage'
  DamageType: SHARP
  BaseValue: 0
  Formatting:
    Additive: '+<value> Sharp Damage'
    Multiply: '+<value> Sharp Damage'
    Compound: 'x<value> Sharp Damage'

```
#### `FIRE_RESISTANCE`
Configured to grant resistance to the FIRE, FIRE_TICK [DamageCause](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/DamageCause).
```yml
FIRE_RESISTANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Fire Resistance'
  Formatting:
    Additive: '+<value> Fire Resistance'
    Multiply: '+<value> Fire Resistance'
    Compound: 'x<value> Fire Resistance'
  Type: DAMAGE_MODIFIER
  Triggers:
    - DAMAGED
  Conditions:
    - (damageCause FIRE || damageCause FIRE_TICK)
  ExecutionPoint: PRE
  DamageFormula: 'd * (1 - v)'
  MaxValue: 1
  MinValue: 0

```
#### `SPEED`
May be used in the [MOVEMENT_SPEED](#movement_speed) stat calculation to affect speed with a formula.
```yml
SPEED:
  Enabled: true
  AlwaysActive: false
  Type: STATIC
  FormulaKey: 'SPD'
  Formatting:
    Additive: '+<value> Speed'
    Multiply: '+<value>% Speed'
    Compound: 'x<value>% Speed'
```
#### `ICE_DAMAGE`
Here is a more complex example that also involves TriggerStats
```yaml
ICE_DAMAGE:
  Enabled: true
  Type: DAMAGE_MODIFIER
  Priority: 50
  Triggers:
    - ATTACK
  ExecutionPoint: PRE
  Display: '&f֍'
  DamageType: ALL
  BaseValue: 0
  TriggerStats:
  - LIGHTNING_DEFENSE LD
  - AIR_DEFENSE AD
  - EARTH_DEFENSE ED
  - FIRE_DEFENSE FD
  - AETHER_DEFENSE AE
  - VOID_DEFENSE VD
  DamageFormula: '1 + d * ( LD + AD - ED - FD + 0.5 * ( AE - VD ) ) / 100'
  Formatting:
    Rounding: 2
    Additive: '&a+<value>'
    Multiply: '&a+<value>%'
    Compound: '&ax<value>%'
```
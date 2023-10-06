# Introduction

Stats are values that affect all kinds of mechanisms, are for Players, Mobs, Items, Skills, etc and can be used for combat, utility, or any case you can think of. Stats can be complicated but learning them is worth the trouble for the powerful things you can do with them.  

Stats are defined in the file `stats.yml`. This file can exist in the root directory of MythicMobs `(Plugins/MythicMobs)` or in a Pack folder. `(Plugins/MythicMobs/Packs/CoolPack)`

# Configuring a Mob with Stats:

It's important to be aware that players get their base value from the `stats.yml` file, while mobs get only some of their base values from the `stats.yml` file.


In this example, you will see that there are 3 stats here actually, Health and Damage are also stats, and natively handled in the typical format of a mob's configuration.
```yml
Some_Mob:
  Health: 50
  Damage: 10
  Stats:
  - CRITICAL_STRIKE_CHANCE 0.2
```

Other stats that work this way are: `ATTACK_DAMAGE`, `ATTACK_SPEED`, `HEALTH`, and `MOVEMENT_SPEED`.


# Custom Stat Types:
|Type|Description|
|-|-|
|STATIC | a static value, does nothing. but can be referenced with placeholders |
|DAMAGE_BONUS | this stat adds a flat amount of bonus damage. |
|DAMAGE_MODIFIER | modifies the damage using a formula |
|PROC | a chance to execute skills |

# Custom Stat Type Options

### DAMAGE_MODIFIER

|Type|Description|
|-|-|
|DamageType|specify a custom damage type|
|Conditions|specify conditions which can affect the Modifier|
|DamageFormula|define a formula for how the damage is modified. See [HERE](#FIRE_RESISTANCE) for an example of this.|

### DAMAGE_BONUS

|Type|Description|
|-|-|
|DamageType|specify a custom damage type|

### All Stat Types
|Type|Description|
|-|-|
| MinValue | Minimum value for the stat|
| MaxValue | Max value for the stat|
| Triggers | what triggers the stat effect, usually just ATTACK or DAMAGED|
| FormulaKey | a key you can use in formulas when this stat is the parent of another|
| ParentStats | a list of other stats that this stat relies on|
| Formula | a formula for the base value if this stat has parent stats|
| BaseValue | a static base value if it doesn't have parents|
| ExecutionPoint | for stats that modify a trigger, can be PRE or POST. determines whether the stat is evaluated before or after any mechanics |



# Modifiers
Modifiers can be used to adjust stats after their base value is defined.
|Modifier|Description|
|-|-|
|ADDITIVE|Adds to the base value of a stat|
|ADDITIVE_MULTIPLIER|adds a multiplier the base value of a stat|
|COMPOUND_MULTIPLIER|multiplies the base value of a stat, then adds it to the base value.|
|SETTER|Overrides all modifiers and base values, and forces the stat to be what is defined.|

Note that stat modifiers can be applied to/by mobs, players, items, enchants, and auras.

<!--
TODO: define mechanics that can manipulate modifiers
-->

In the case of `ADDITIVE_MULTIPLIER` and `COMPOUND_MULTIPLIER`, the difference is easy to misunderstand; However, this example should make it a bit more clear:

lets say you have these modifiers:
 ``` rb
  10 additive
  5 multiply
  3 multiply
  2 compound
  base value of 0
```
the resulting math MythicMobs would calculate this is as follows:

```rb
10 * (5 + 3) * 2 = 160
```

This shows how regular multipliers are additive, and compound multipliers are multiplicative. you can think of it as "+10%" vs. "x10%"



# Examples

## Built-In Stats

These stats are inherently supported by MythicMobs.

 #### `ACCURACY`
Chance for an attack to land damage. Reduces opponent's [DODGE_CHANCE](#dodge_chance).
```yml
ACCURACY:
  Enabled: false
  AlwaysActive: false
  Display: 'Accuracy'
  Tooltips:
    Additive: '+<value> Accuracy'
    Multiply: '+<value> Accuracy'
    Compound: 'x<value> Accuracy'
  BaseValue: 0
```
 #### `ATTACK_DAMAGE`
Base Damage Output
```yml
ATTACK_DAMAGE:
  Enabled: true
  AlwaysActive: false
  Display: 'Damage'
  Tooltips:
    Additive: '+<value> Damage'
    Multiply: '+<value> Damage'
    Compound: 'x<value> Damage'
  BaseValue: 1
```
 #### `ATTACK_SPEED`
Attack cooldown frequency. Typically only used for Players.
```yml
ATTACK_SPEED:
  Enabled: true
  AlwaysActive: false
  Display: 'Attack Speed'
  Tooltips:
    Additive: '+<value> Attack Speed'
    Multiply: '+<value> Attack Speed'
    Compound: 'x<value> Attack Speed'
  BaseValue: 4.0
```
 #### `BONUS_DAMAGE`
Additional Modifier for dealing extra damage
```yml
BONUS_DAMAGE:
  Enabled: false
  AlwaysActive: false
  Display: 'Bonus Damage'
  Tooltips:
    Additive: '+<value> Bonus Damage'
    Multiply: '+<value> Bonus Damage'
    Compound: 'x<value> Bonus Damage'
  BaseValue: 0
```
 #### `CRITICAL_STRIKE_CHANCE`
 Chance to land a Critical Strike (Chance-based Crit)
```yml
CRITICAL_STRIKE_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Critical Strike'
  Tooltips:
    Additive: '+<value> Critical Strike'
    Multiply: '+<value> Critical Strike'
    Compound: 'x<value> Critical Strike'
  BaseValue: 0
  MinValue: 0
  Skills:
  - particles{p=crit;a=50;hS=1;y=1;s=1} @trigger
```
 #### `CRITICAL_STRIKE_DAMAGE`
 Damage dealt via Critical Strike
```yml
CRITICAL_STRIKE_DAMAGE:
  Enabled: false
  AlwaysActive: true
  Display: 'Critical Damage'
  Tooltips:
    Additive: '+<value> Critical Damage'
    Multiply: '+<value> Critical Damage'
    Compound: 'x<value> Critical Damage'
  BaseValue: 1
```
 #### `CRITICAL_STRIKE_RESILIENCE`
 Resistance to Critical Strike
```yml
CRITICAL_STRIKE_RESILIENCE:
  Enabled: false
  Display: 'Resilience'
  AlwaysActive: false
  Tooltips:
    Additive: '+<value> Resilience'
    Multiply: '+<value> Resilience'
    Compound: 'x<value> Resilience'
  BaseValue: 0
```
 #### `DAMAGE_REDUCTION`
 Generic damage reduction
```yml
DAMAGE_REDUCTION:
  Enabled: false
  AlwaysActive: false
  Display: 'Damage Reduction'
  Tooltips:
    Additive: '+<value> Damage Reduction'
    Multiply: '+<value> Damage Reduction'
    Compound: 'x<value> Damage Reduction'
  BaseValue: 0
```
 #### `DEFENSE`
 Defense
```yml
DEFENSE:
  Enabled: false
  AlwaysActive: false
  Display: 'Defense'
  Tooltips:
    Additive: '+<value> Defense'
    Multiply: '+<value> Defense'
    Compound: 'x<value> Defense'
  BaseValue: 0
```
 #### `DODGE_CHANCE`
 Chance for an attack to fail when attempting to damage. Reduces opponent's [ACCURACY](#accuracy).
```yml
DODGE_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Dodge'
  Tooltips:
    Additive: '+<value> Dodge Chance'
    Multiply: '+<value> Dodge Chance'
    Compound: 'x<value> Dodge Chance'
  BaseValue: 0
  Skills: []
```
 #### `EXPERTISE`
Affects and lowers the [PARRY_CHANCE](#parry_chance) of the opponent.
```yml
EXPERTISE:
  Enabled: false
  AlwaysActive: false
  Display: 'Expertise'
  Tooltips:
    Additive: '+<value> Expertise'
    Multiply: '+<value> Expertise'
    Compound: 'x<value> Expertise'
  BaseValue: 0
```
 #### `HEALTH`
 Health values
```yml
HEALTH:
  Enabled: false
  AlwaysActive: true
  Display: 'Health'
  Tooltips:
    Additive: '+<value> Health'
    Multiply: '+<value> Health'
    Compound: 'x<value> Health'
  BaseValue: 20
  MinValue: 1
```
 #### `HEALTH_REGENERATION`
 Rate of Health Regeneration
```yml
HEALTH_REGENERATION:
  Enabled: false
  AlwaysActive: false
  Display: 'Health Regeneration'
  Tooltips:
    Additive: '+<value> Regeneration'
    Multiply: '+<value> Regeneration'
    Compound: 'x<value> Regeneration'
  BaseValue: 0
  MaxValue: 1000000
  MinValue: 0
  Frequency: 60
```
 #### `LIFESTEAL_CHANCE`
 Chance for damage dealt to heal the attacker
```yml
LIFESTEAL_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Lifesteal Chance'
  Tooltips:
    Additive: '+<value> Lifesteal Chance'
    Multiply: '+<value> Lifesteal Chance'
    Compound: 'x<value> Lifesteal Chance'
  BaseValue: 0
```
 #### `LIFESTEAL_POWER`
 How much healing LifeSteal does.
```yml
LIFESTEAL_POWER:
  Enabled: true
  AlwaysActive: false
  Display: 'Lifesteal Power'
  Tooltips:
    Additive: '+<value> Lifesteal Power'
    Multiply: '+<value> Lifesteal Power'
    Compound: 'x<value> Lifesteal Power'
  BaseValue: 0.1
```
 #### `MOVEMENT_SPEED`
 Movement Speed.
```yml
MOVEMENT_SPEED:
  Enabled: false
  AlwaysActive: true
  Display: 'Movement Speed'
  Tooltips:
    Additive: '+<value> Movement Speed'
    Multiply: '+<value>% Movement Speed'
    Compound: 'x<value>% Movement Speed'
  ParentStats:
  - SPEED
  Formula: '0.2 + (0.2 / (1 + e^(-0.005 * (SPD - 1000))))'

```
 #### `PARRY_CHANCE`
 Chance to mitigate and reflect damage from sources that melee you from the front.
```yml
PARRY_CHANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Parry Chance'
  BaseValue: 0
  Priority: 0
  Tooltips:
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
 #### `PARRY_POWER`
 How much damage is mitigated by Parry.
```yml
PARRY_POWER:
  Enabled: false
  AlwaysActive: false
  Display: 'Parry Power'
  BaseValue: 0.5
  Tooltips:
    Additive: '+<value> Parry Power'
    Multiply: '+<value> Parry Power'
    Compound: 'x<value> Parry Power'

```
 #### `PARRY_COUNTERATTACK`
 How much damage is returned to the opponent when parrying.
```yml
PARRY_COUNTERATTACK:
  Enabled: false
  AlwaysActive: false
  Display: 'Parry Counterattack'
  BaseValue: 1
  Tooltips:
    Additive: '+<value> Parry Counterattack'
    Multiply: '+<value> Parry Counterattack'
    Compound: 'x<value> Parry Counterattack'

```

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
  Tooltips:
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
  Tooltips:
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
  Tooltips:
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
  Tooltips:
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
  Tooltips:
    Additive: '+<value> Sharp Damage'
    Multiply: '+<value> Sharp Damage'
    Compound: 'x<value> Sharp Damage'

```
#### `FIRE_RESISTANCE`
Resistance to the FIRE, FIRE_TICK [DamageCause](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/DamageCause).
```yml
FIRE_RESISTANCE:
  Enabled: false
  AlwaysActive: false
  Display: 'Fire Resistance'
  Tooltips:
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
Is used in the [MOVEMENT_SPEED](#movement_speed) stat calculation to affect speed with a formula.
```yml
SPEED:
  Enabled: true
  AlwaysActive: false
  Type: STATIC
  FormulaKey: 'SPD'
  Tooltips:
    Additive: '+<value> Speed'
    Multiply: '+<value>% Speed'
    Compound: 'x<value>% Speed'
```
The enchantments attribute is used to apply enchantments to items made using MythicMobs.
Any of these can be put on any item and can exceed natural enchantment-level limits set by Minecraft.
Some enchantments may not have any effects if put on items that they weren't made for.

Syntax
------
```yml
internal_itemname:
  Id: <material>
  Enchantments:
  - <enchantment>:<level>
  - <enchantment>:<level>
  - ...
```
**\<enchantment>**  
Type of enchantment to be applied to the specified item.

**\<level>**  
The level of the specified enchantment.

Available Enchantments
----------------------

A list of available [enchantments](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html) can be found on spigot javadocs

Example
-------
```yml
lethal_pickaxe:
  Id: diamond_pickaxe
  Enchantments:
  - DAMAGE_ALL:3
  - KNOCKBACK:1
```

<!--
**ARROW\_DAMAGE**

-   "Power"
-   Used on bows.
-   Provides extra base damage when shooting arrows from bows.
-   Use this rather than "Damage: " option to increase damage for bows.
-   Vanilla Max: 5

**ARROW\_FIRE**

-   "Flame"
-   Used on bows.
-   Sets target on fire.
-   Vanilla Max: 1

**ARROW\_KNOCKBACK**

-   "Punch"
-   Used on bows.
-   Knock mob back further.
-   Can knockback mobs with 100% KnockbackResistance
-   Vanilla Max: 2

**ARROW\_INFINITE**

-   "Infinity"
-   Used on bows.
-   Bow doesn't use arrows (need one arrow in inventory)
-   Vanilla Max: 1

**DAMAGE\_ALL**

-   "Sharpness"
-   Used on melee weapons.
-   Increases damage with melee weapons to all mobs.
-   Adds 1.25 damage per level.
-   Vanilla Max: 5

**DAMAGE\_ARTHROPODS**

-   "Bane of Arthropods"
-   Used on melee weapons.
-   Increases damage with melee weapons to spiders, cave spiders,
silverfish
-   Adds 2.5 damage per level.
-   Vanilla Max: 5

**DAMAGE\_UNDEAD**

-   "Smite"
-   Used on melee weapons.
-   Increases damage with melee weapons to undead
-   Adds 2.5 damage per level.
-   Vanilla Max: 3

**CHANNELING**

-   "Channeling"
-   Used on tridents.
-   If raining, strikes with lightning on impact with mob.
-   Vanilla Max: 1

**SWEEPING\_EDGE**

-   "Sweeping Edge"
-   Used on swords.
-   Increases the damage from sword sweep attacks.
-   Higher damage per level.
-   Vanilla Max: 3

**DIG\_SPEED**

-   "Efficiency"
-   Used on tools.
-   Increase dig speed by 30% over previous level.
-   Vanilla Max: 5

**DURABILITY**

-   "Unbreaking"
-   Used on all items that have durability.
-   For most items (other than armor) lasts Level + 1 times as long
-   For armor, lasts 25%/36%/43% longer.
-   Vanilla Max: 3

**MENDING**

-   "Mending"
-   Used on all items that have durability.
-   Repairs item using picked up XP.
-   2 durability per XP.
-   Vanilla Max: 1

**FIRE\_ASPECT**

-   "Fire Aspect"
-   Used on melee weapons.
-   Adds 3 burn ticks per level to melee weapons.
-   Vanilla Max: 2

**IMPALING**

-   "Impaling"
-   Used on melee weapons.
-   Deals extra damage to
[aquatic](https://minecraft.gamepedia.com/Mob#Underwater_Mobs) mobs
.
-   Does more damage per level.
-   Vanilla Max: 5

**KNOCKBACK**

-   "Knockback"
-   Used on melee weapons.
-   Adds additional knockback to melee attacks. (Can knockback mobs with
100% KnockbackResistance)
-   Vanilla Max: 2

**LOOT\_BONUS\_BLOCKS**

-   "Fortune"
-   Used on axes, shovels and pickaxes.
-   Increase chances of looting multiple rare blocks or rare items from
blocks.
-   Vanilla Max: 3

**LOOT\_BONUS\_MOBS**

-   "Looting"
-   Used on melee weapons.
-   Increases maximum loot by 1 per level.
-   Increase chance for rare loot by 0.5% per level
-   Vanilla Max: 3

**LOYALTY**

-   "Loyalty"
-   Used on tridents.
-   Causes the trident to return when thrown.
-   Vanilla Max: 3

**OXYGEN**

-   "Respiration"
-   Used on helmets.
-   Increase breathing time by 15 per level, decreases suffocation
damage and improves underwater vision
-   Vanilla Max: 3

**PROTECTION\_ENVIRONMENTAL**

-   "Protection"
-   Used on armor.
-   Protects against all damage taken after normal armor is taken into
account.
-   Vanilla Max: 4

**PROTECTION\_FALL**

-   "Feather Falling"
-   Used on boots.
-   Protects against fall damage taken after normal armor is taken into
account.
-   Vanilla Max: 4

**PROTECTION\_FIRE**

-   "Fire Protection"
-   Used on armor.
-   Protects against fire damage taken after normal armor is taken into
account.
-   Reduces burn duration
-   Vanilla Max: 4

**PROTECTION\_PROJECTILE**

-   "Projectile Protection"
-   Used on armor.
-   Protects against projectile damage taken after normal armor is taken
into account.
-   Vanilla Max: 4

**PROTECTION\_EXPLOSIONS**

-   "Blast Protection"
-   Used on armor.
-   Protects against explosive damage taken after normal armor is taken
into account.
-   Reduces knockback from explosions.
-   Vanilla Max: 4

**RIPTIDE**

-   "Riptide"
-   Used on tridents.
-   If raining or in water, launches player in direction of thrown
trident.
-   Higher levels increase speed.
-   Vanilla Max: 3

**SILK\_TOUCH**

-   "Silk Touch"
-   Used on tools.
-   Allows player to obtain items which normally can't be obtained.
-   Same effect on all levels.
-   Vanilla Max: 1

**THORNS**

-   "Thorns"
-   Used on armor.
-   ```Level X 15%``` chance of inflicting attacker for 1 to 4 damage.
-   Does not stack on multiple pieces.
-   Vanilla Max: 3

**WATER\_WORKER**

-   "Aqua Affinity"
-   Used on helmets.
-   Allows player to break blocks underwater at regular speed.
-   Vanilla Max: 1

**DEPTH\_STRIDER**

-   "Depth Strider"
-   Used on boots.
-   Allows player to move faster in water.
-   Vanilla Max: 3

**FROST\_WALKER**

-   "Frost Walker"
-   Used on boots.
-   Freezes water under the players feet.
-   Increases radius with higher levels.
-   Vanilla Max: 2

**BINDING\_CURSE**

-   "Curse of Binding"
-   Used on most items.
-   Items with curse can't be removed. (Except by dying)
-   Vanilla Max: 1

**VANISHING\_CURSE**

-   *Curse of Vanishing*
-   Used on most items.
-   Items with curse vanish when player dies.
-   Vanilla Max: 1

**MULTISHOT**

-   "Multishot"
-   Used on crossbows.
-   Fires 3 arrows as opposed to 1.
-   Vanilla Max: 1

**PIERCING**

-   "Piercing"
-   Crossbow projectiles pierce entities.
-   Vanilla Max: 4

**QUICK_CHARGE**

-   "Quick Charge"
-   Charges crossbows quickly.
-   Vanilla Max: 3

**SOUL_SPEED**

-   "Soul Speed"
-   Walk quicker on soul blocks.
-   Vanilla Max: 3

-->
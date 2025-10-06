The Drops tag can be added to your custom mobs to allow them to drop items of your choice upon their death. There are three types of custom drops available in MythicMobs to distinguish between.


[[_TOC_]]


Drops are the simplest way to implement custom drops.

## Drops Configuration
```yaml
internal_mobname:
  Type: <mobtype>
  Drops:
  - <drop> <amount> <chance>
  - <drop> <amount> <chance>
  - ...
```

### Drop
Can be either an item from MythicMobs, a vanilla item, exp, a drop table or an item/experience for a supported plugin. The list of available [Drop Types](Drops#drop-types) is displayed below

### Amount
The amount of items to be dropped.  

Can be a number range, for example: `1-3` or `1to3`.  
In this case, the number of dropped items will never be smaller than the leftmost number and never be **equal or greater** to the rightmost number
> Writing `1to3` will drop at least 1 item and at most 2 items

### Chance
The chance for the specified item to be dropped.
  - Must be a number between 0 and 1 
  - **Note:** allows percentage chances. (10% instead of 0.1).

## Drop Types
| **Type**                    | **Explanation**                                          | **Example**                             |
|-----------------------------|----------------------------------------------------------|-----------------------------------------|
| [MythicMob](/drops/DropTypes/MythicMob)| Will drop a MythicMob                         |                |
| [Mythic Item](/drops/DropTypes/MythicItem)| Will drop a Mythic Item                    |                |
| [VanillaLootTable](/drops/DropTypes/VanillaLootTable) | Drop items from vanilla loot tables and datapacks | `- vanillaLootTable minecraft:table_name` |
| **champions-exp**           | Will drop experience points for the plugin `Champions`.  |                                         |
| [skillapi-exp](/drops/DropTypes/SkillAPIExp)| Will drop experience points for the plugin `SkillAPI` |                                         |
| **heroesexp**               | Will drop experience points for the plugin `Heroes`.     |                                         |
| [mcmmo-exp](/drops/DropTypes/McMMOExp)| Will drop experience points for the plugin `MCMMO`. | `- mcmmo-exp 69`                       |
| **exp**                     | Will drop regular Minecraft experience points.           | `- exp 420`                                         |
| [money](/drops/DropTypes/Money)| Will drop money for the plugin `Vault`.               | `- money 1500`                                        |
| **mythicdrop &lt;item&gt;** | Will drop an &lt;item&gt; from the plugin `MythicDrops`. | `- mythicdrop CoolSword 1`                                        |
| [phatloot](/drops/DropTypes/PhatLoot)| Will drop an &item from the plugin `PhatLoot`.    | `- phatloot LootTableName 1`                                        |
| [command](/drops/DropTypes/Command)| Will run a command in console.                    | `- cmd{c="warp <trigger.name> spawn"} 1`  |
| [mmoitems](https://gitlab.com/phoenix-dvpmt/mmoitems/-/wikis/Item%20Drop%20Tables#adding-mmoitems-to-mythicmobs-drop-tables)    | Drops a `mmoitems` item                                    | `- mmoitems{type=SWORD;id=CUTLASS} 1 1` |
| **nothing**                 | Will drop nothing. Can help while creating weighted droptables | `- nothing`                                        |
| [ItemVariable](/drops/DropTypes/ItemVariable)| Drops the item defined in the specified item variable    | `- itemvariable{variable=caster.stolenitem} 1 1`|


### Example
This example will have a 20% chance of dropping 3 diamonds, a 60% chance to run a command and a 12% chance to drop between 100 and 600 exp
```yaml
YourMob:
  Type: ZOMBIE
  Drops:
  - diamond 3 0.2
  - cmd{c="crate give <trigger.name> RewardCrate 1"} 1 0.6
  - exp 100to600 0.12
```
## In-line Drops

For very basic equipment, you can add some inline item data so that you don't always have to create a mythic item.
You can use all the item data from [Inline Item Configurations](/Mobs/Equipment#in-line-items)!

```yaml
 Drops:
 - leather_chestplate{name="Dark Leather";lore="&8A vest made of darkened leather";color=BLACK} 1 1
```

### Example
The below drops section will drop a Panda player head item that has 2 enchants on it, and will drop 3 pieces of diamond armor that all have names, lore, and enchantments on them!

```yaml
  Drops:
  - PLAYER_HEAD{skullTexture=eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjY0NjNlNjRjZTI5NzY0ZGIzY2I0NjgwNmNlZTYwNmFmYzI0YmRmMGNlMTRiNjY2MGMyNzBhOTZjNzg3NDI2In19fQ==;enchants=WATER_WORKER:1,OXYGEN:3} 1 1
  - DIAMOND_CHESTPLATE{name="Panda<&sq>s Will";lore="A Panda must be vigilant";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} 1 1
  - DIAMOND_LEGGINGS{name="Panda<&sq>s Strength";lore="A Panda must be strong";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} 1 1
  - DIAMOND_BOOTS{name="Panda<&sq>s Speed";lore="A Panda must be fast";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,PROTECTION_FALL:4,DEPTH_STRIDER:3} 1 1
```
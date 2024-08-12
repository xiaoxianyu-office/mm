The Equipment section in a mob config defines what kind of equipment the mob will spawn with. The equipment will only be applied to the mob when it spawns or during a reload, and can be changed afterwards by using the [Equip mechanic](/skills/mechanics/equip).

If the PreventOtherDrops option is not enabled, then the mob will naturally drop all of its equipped items on death.

If you want your mob to not wear any equipment, you can use the option "PreventRandomEquipment". See [Mob Options](/Mobs/Options). An alternative to using that option is to equip your mob with *dummy items*, such as AIR.

Equipment slots can also accept [droptables](/drops/DropTables#equipment-droptables), allowing for the creation of "sets" where a random item is selected from the set. For example, a droptable can be created that contains every vanilla helmet, which can then be used on the mob in the equipment tab to select one random helmet to wear.

[[_TOC_]]

## Syntax
```yaml
internal_mobname:
  Type: <mobtype>
  Equipment:
  - <item> <slot>
  - <item> <slot>
  - ...
```

### Item  
Can be either the name of a [MythicMobs item](/Items/Items#internal_name) or a vanilla item.

### Slot 
Defines the slot on the mob that item should be carried on.

| Slot    | Description                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| HEAD    | The head slot. Accepts regular helmets, playerheads, and even blocktypes.                    |
| CHEST   | The chest slot. Will only render chestplates, but will carry any items.                      |
| LEGS    | The leg slot. Will only render leggings, but will carry any items.                           |
| FEET    | The feet slot. Will only render boots, but will carry any items.                             |
| HAND    | The mainhand (right) hand slot.                                                              |
| OFFHAND | The offhand (left) hand slot.                                                                |

```yaml
awesome_boss:
  Type: pig_zombie
  Equipment:
  - awesome_boss_helmet HEAD
  - diamond_sword HAND
```

## In-line Items
For very basic equipment, you can add some inline item data so that you don't always have to create a mythic item.
All the inline item data that works under `Equipment` will also work under the [Drops](/drops/Drops) section.

```yaml
 Equipment:
 - leather_chestplate{name="Dark Leather";lore="&8A vest made of darkened leather";color=BLACK} CHEST
```

### Available inline attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name      | display, n, d | The display name of the item                                     |         |
| data      |           | The "Data" of the item, to not be confused with CustomModelData      | 0       |
| model     |           | The CustomModelData of the item                                      | 0       |
| amount    | a         | The amount of the item                                               | 1       |
| lore      | l         | The lore of the item                                                 |         |
| enchantments | enchants, ench, e | A list of [enchantments] of the item                      |         |
| potioneffects | peffects, potion, pe | A list of [potion effects] of the item, if a potion   |         |
| color     | c, potioncolor, pcolor, pc | The color of the item, if a potion                  |         |
| skullowner |          | The owner of the item, if a skull                                    |         |
| skulltexture |        | The SkinURL of the texture of the item, if a skull                   |         |

[enchantments]: /Items/Enchantments
[potion effects]: /Items/Potions


## MMOItems
To equip a mob with an mmoitem, use the following syntax:
```yaml
  Equipment:
  - mmoitems{type=ARMOR;id=STEEL_HELMET} HEAD
  - mmoitems{type=ARMOR;id=STEEL_CHESTPLATE} CHEST
  - mmoitems{type=ARMOR;id=STEEL_LEGGINGS} LEGS
  - mmoitems{type=ARMOR;id=STEEL_BOOTS} FEET
  - mmoitems{type=SWORD;id=RUBY_SWORD} HAND
```
Please note that mmo stats on the armor DO NOT work on MythicMobs. As such, they will not have extra health, defense or attack damage because of it.


## Examples
The example below will spawn a zombie with a panda player head equipped in their head slot.
```yaml
PandaZombie:
  Type: ZOMBIE
  Options:
    PreventSunburn: true
  Equipment:
  - PLAYER_HEAD{skullTexture=eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjY0NjNlNjRjZTI5NzY0ZGIzY2I0NjgwNmNlZTYwNmFmYzI0YmRmMGNlMTRiNjY2MGMyNzBhOTZjNzg3NDI2In19fQ==} HEAD
```

Now lets take this Panda Zombie and give it some custom armor with a name, lore, and enchantments.

```yaml
PandaZombie:
  Type: ZOMBIE
  Options:
    PreventSunburn: true
  Equipment:
  - PLAYER_HEAD{skullTexture=eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjY0NjNlNjRjZTI5NzY0ZGIzY2I0NjgwNmNlZTYwNmFmYzI0YmRmMGNlMTRiNjY2MGMyNzBhOTZjNzg3NDI2In19fQ==;enchants=WATER_WORKER:1,OXYGEN:3} HEAD
  - DIAMOND_CHESTPLATE{name="Panda<&sq>s Will";lore="A Panda must be vigilant";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} CHEST
  - DIAMOND_LEGGINGS{name="Panda<&sq>s Strength";lore="A Panda must be strong";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} LEGS
  - DIAMOND_BOOTS{name="Panda<&sq>s Speed";lore="A Panda must be fast";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,PROTECTION_FALL:4,DEPTH_STRIDER:3} FEET
```

Lastly, remember that we can use the inline item data in the drops section. Killing the PandaZombie will make it drop all of the items, with their names, lore, and enchants all without the need to make any mythic items!

```yaml
PandaZombie:
  Type: ZOMBIE
  Options:
    PreventSunburn: true
  Equipment:
  - PLAYER_HEAD{skullTexture=eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjY0NjNlNjRjZTI5NzY0ZGIzY2I0NjgwNmNlZTYwNmFmYzI0YmRmMGNlMTRiNjY2MGMyNzBhOTZjNzg3NDI2In19fQ==;enchants=WATER_WORKER:1,OXYGEN:3} HEAD
  - DIAMOND_CHESTPLATE{name="Panda<&sq>s Will";lore="A Panda must be vigilant";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} CHEST
  - DIAMOND_LEGGINGS{name="Panda<&sq>s Strength";lore="A Panda must be strong";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} LEGS
  - DIAMOND_BOOTS{name="Panda<&sq>s Speed";lore="A Panda must be fast";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,PROTECTION_FALL:4,DEPTH_STRIDER:3} FEET
  Drops:
  - PLAYER_HEAD{skullTexture=eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjY0NjNlNjRjZTI5NzY0ZGIzY2I0NjgwNmNlZTYwNmFmYzI0YmRmMGNlMTRiNjY2MGMyNzBhOTZjNzg3NDI2In19fQ==;enchants=WATER_WORKER:1,OXYGEN:3} 1 1
  - DIAMOND_CHESTPLATE{name="Panda<&sq>s Will";lore="A Panda must be vigilant";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} 1 1
  - DIAMOND_LEGGINGS{name="Panda<&sq>s Strength";lore="A Panda must be strong";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,THORNS:2} 1 1
  - DIAMOND_BOOTS{name="Panda<&sq>s Speed";lore="A Panda must be fast";enchants=PROTECTION_ENVIRONMENTAL:4,DURABILITY:3,MENDING:1,PROTECTION_FALL:4,DEPTH_STRIDER:3} 1 1
```
All available options will be listed here.
These options must be placed under the `Options:` tag inside your item configurations.
```yml
example_item:
  Id: diamond
  Options:
    SomeOption: value
```

# Universal Options
These options are applicable to all items:

#### Repairable
Sets the repair cost of the item to maximum, making it completely uneditable in anvils and/or enchantment tables.  
Will override the RepairCost option.  
Defaults to `false`.
```yaml
  Options:
    Repairable: false
```  

#### RepairCost
Sets the repair cost of the item.  
If set to less than 0, the vanilla one will be used.  
Defaults to `-1`.  
```yaml
  # Not an option, apparently, but kept here because of repairable
  RepairCost: 10
```

#### Unbreakable
Sets the unbreakable tag on the item.  
Items with this set to true will not lose durability.  
Defaults to `false`.  
```yaml
  Options:
    Unbreakable: true
```


#### Glint
Adds the enchantment glint visual effect to an item
Defaults to `false`.  
```yaml
  Options:
    Glint: true
```

#### HideFlags
**Note: this feature does not exist >=1.20.5!** [Use this instead](/Items/Items#hide)

Hides all the item flags, making things like enchants not visible in the item's lore (please note however that the item will still have an enchanted glow).  
Defaults to `false`.
```yaml
  Options:
    HideFlags: true
```

#### PreventStacking
Prevents the item from stacking to similar items.  
Defaults to `false`.  
```yaml
  Options:
    PreventStacking: true
```

#### StackSize
Sets the maximum stack size of the item in the inventory. Does not work when used alongside attributes.
```yaml
  Options:
    StackSize: 16
```

#### GenerateUUID
Applies a random UUID to the item upon generation. Useful to easily detect duped items. Enabling this option automatically prevents similar items from stacking, as they share different UUIDs.
```yaml
  Options:
    GenerateUUID: true
```

#### GenerateTimestamp
Applies the current unix time to the item on generation. Useful to backtrack the exact time an item was created. Enabling this option will prevent items from stacking if they were generated at different times.
```yaml
  Options:
    GenerateTimestamp: true
```


#### ItemModel
The model that should be applied to the item, which [works like this item component](https://minecraft.wiki/w/Data_component_format#item_model)
```yaml
MODELED_ITEM:
  Id: PAPER
  Display: '&dKing Helmet'
  Options:
    ItemModel: SomeModel
```

#### FireResistant
Whether the item is resistant to fire, as netherite is.  
Defaults to `false`.  
```yaml
  Options:
    FireResistant: true
```

# Playerheads
Only applicable to playerhead type items

#### Player
Sets the texture of the player head.  
The value must be the IGN of the target player.  
Player heads must use data value 3 for this to work.  
```yaml
  Options:
    Player: Herobrine
```

#### SkinTexture
Also sets the texture of the player head, but instead uses a SkinURL.  
> - Type into browser: https://sessionserver.mojang.com/session/minecraft/profile/trimmeduuidofplayerhere.  
> - Use http://mcuuid.net/ to find the trimmed uuid of the player.  

Player heads must use data value 3 for this to work.  
This option also supports hashes.  
```yaml
  Options:
    SkinTexture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvODdlMGFhOTQzM2RiYTliNzU5MzJhMTFkYzk0ZDQwNmJkZTE5ZTg2MzUxNDIxNDkyYjNlZDM3OGM4ZTFhN2NjIn19fQ==
```

### SkinURL
The URL to the skin

```yaml
TestHeadURL:
  Id: PLAYER_HEAD
  Options:
    Placeable: true
    SkinURL: "https://textures.minecraft.net/texture/1c45ee6a2592e890f2aaa5a68aaa98f9e2f964327c15d18fdf7665c577af23cc" 
```

#### SkinID
The ID of the skin. It's the last part of the canonical [skin URL](#skinurl)

```yaml
TestHeadID:
  Id: PLAYER_HEAD
  Options:
    Placeable: true
    SkinID: 1c45ee6a2592e890f2aaa5a68aaa98f9e2f964327c15d18fdf7665c577af23cc
```


# Dyeable Items

#### Color
Dyes the armor piece to a color according to RGB settings. 0-255.  
Alternately can use a predefined color. Found [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html).  
Can pick colors using the Paint program on Windows. Open it up then choose "Edit Colors" to get your RGB value.  
Only usable on leather armor type, banners, shields and such.
```yaml
  Options:
    Color: RED
```
```yaml
  Options:
    Color: 102,102,153
```


# Examples
```yaml
ClothSlippers:
  Id: 301
  Data: 0
  Display: '&fCloth Slippers'
  Lore:
  - ''
  - 'So Soft!'
  - ''
  Enchantments:
  - DURABILITY:1
  Options:
    Color: 200,200,200
```
Lots of possible options included:
```yaml
TestHead:
  Id: 397
  Data: 3
  Options:
    Player: Rickyling
```
```yaml
dat_item_though:
  Id: banner
  Data: 4
  Display: '&c&lThe Banner&r'
  Lore:
  - ''
  - '&rIt<&sq>s the perfect stone.'
  - '&cNever question that.'
  - ''
  Amount: 8
  Options:
    Color: 200,200,200
    Unbreakable: true
  Enchantments:
  - DURABILITY:1
  - ARROW_FIRE:10
```
An example of a firework rocket
```yaml
FireworkGoBoom:
  Id: FIREWORK_ROCKET
  Display: 'Rocket'
  Firework:
    Colors:
    - 255,0,255
    - 0,0,0
    FadeColors:
    - 200,0,0
    Flicker: true
    Trail: true
```
![](http://fs5.directupload.net/images/160306/or6m6n2s.jpg)

Making custom items in Mythic Mobs is quite easy.
Unlike mobs and skills however, items made with this plugin do not come with any special or unique options.
Any items you create with MythicMobs could also be created by Minecraft commands,
though making the items using the MythicMobs configurations is much more comfortable.

Of the following options available for items, only `internal_name` and `Id` are required. All other options/attributes are completely optional.

You can make any number of files in the `\plugins\MythicMobs\Items` folder, and they can be
named anything you like as long as the file ends in .yml.

Breaking Down The Item Configuration
-------------------------

#### Internal_Name
This string will be how your item is referenced internally in MythicMobs and can be any name you like. 
Must be alphanumeric, **NO SPACES ALLOWED**.
```yml
example_item:
```

#### Id
The base material to use for your item, it can be any valid material that's listed [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html).
```yml
example_item:
  Id: leather_chestplate
```
<!-- 
#### **Data**
Used to specify the *used up* durability points on items.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
```
-->

#### Display
Sets the display name of the item.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
```



#### Lore
Sets the lore of the item. You can generate a random number using `{min-max}`, `<random.#to#>`, or `<random.float.#to#>`.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Lore:
    - <rainbow>This line is a rainbow</rainbow>
    - <red>This line should be red</red>
    - This is a random generated number > <random.-1to50>
    - <gradient:#5e4fa2:#f79459>A really nice gradient</gradient>
    - There are some symbols, like <&sq>, that should never be put as is into a configuration. Use a placeholder!
```

#### CustomModelData
Sets the CustomModelData tag on the item. `Model` is also another alias for `CustomModelData`.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  CustomModelData: 12345
```
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Model: 12345
```

#### **Durability**:
Sets the amount of durability to take off the item. The below example sets a Diamond Sword to have 1461 durability since by default it has 1561.
```yml
example_item:
  Id: diamond_sword
  Durability: 100
  Display: <green>An Example Item</green>
```

#### **Attributes**
Special field that allows the addition of item attributes to certain armor slots. See [Item Attributes](/Items/Attributes).
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Attributes:
    Chest:
      Health: 25
```

#### **Amount**
Sets the default amount of items to give when this item is being called by the plugin.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Amount: 1
```

#### **Options**
A special field that comes with numerous sub-options. See [Item Options](/Items/Options).
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Options:
    AppendType: true
    Color: 255,0,0
```

#### **Enchantments**
Any items can have any enchantments(s).
A list of available enchantments can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html).
See also [enchantments](/items/Enchantments) page on how to configure item enchantments.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Options:
    Color: 255,0,0
  Enchantments:
    - PROTECTION_ENVIRONMENTAL:2
    - THORNS:3
```

#### **Hide**
Special field that allows to hide specific things from the item tooltip.
All possible flags can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Attributes:
    Chest:
      Health: 25
  Enchantments:
    - THORNS:3
  Options:
    Color: 255,0,0
  Hide:
    - ATTRIBUTES
    - ENCHANTS
```

#### **PotionEffects**
Sets the potion effects of the item. These effects won't do anything if the [base item](#id) is not a `potion`, `splash_potion`, `lingering_potion`, or `tipped_arrow`.
See [Potions](/Items/Potions).
```yml
example_item:
  Id: potion
  Display: <#f99cb3>Pink potion
  Options:
    Color: 249,156,179
  PotionEffects:
    - CONFUSION 100 2
```

#### **BannerLayers**
Sets the banner layers of a banner or a shield.
See [Banner Layers](/Items/Banner-Layers).
```yml
example_item:
  Id: yellow_banner
  BannerLayers:
    - RED BASE
    - WHITE CURLY_BORDER
    - WHITE STRIPE_CENTER
```

#### **CanPlaceOn**
Sets what blocks this item can be placed on, if the player is in adventure mode.
```yaml
MyCoolAnvil:
  Id: ANVIL
  CanPlaceOn:
  - diamond_block
```

#### **CanBreak**
Sets what blocks this item can break, if the player is in adventure mode.
```yaml
MyCoolStick:
  Id: STICK
  CanBreak:
  - grass_block
  - diamond_block
  - obsidian
```

#### Group
Sets the group the item is in for `/mm items browse`.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Group: 'Armor'
```

### **NBT**
Sets what NBT tags to put on your items.
This allows cross-over with a lot of other plugins, or just for storing custom information.

Before you add an NBT tag to your items, you have to know [SNBT formatting](https://minecraft.fandom.com/wiki/NBT_format#SNBT_format).
A tag value's type can be changed by adding a prefix to the tag value:

| Prefixes | int/ | float/ | double/ | byte/ | bool/ | boolean/ |
|----------|------|--------|---------|-------|-------|----------|

Let's convert this snbt:  `{name1:123,name2:"sometext1",name3:{subname1:456,subname2:"sometext2"}}` to mythic formatting:

```yml
example_item:
  Id: STICK
  NBT:
    name1: int/123
    name2: sometext1
    name3:
      subname1: int/456
      subname2: sometext2
```

```yml
#An item with MYTHIC_TYPE tag
example_item:
  Id: stick
  NBT:
    MYTHIC_TYPE: example_item
```

```yml
example_item:
  Id: diamond_sword
  NBT:
    CanDestroy:
      - stone
      - dirt
    Base:
      ATag: int/20
      SomeOtherTag: something
    SomeModifier:
      Value: double/0.25
      CanDoThis: boolean/true
    Denizen NBT:
      somedenizentag: a_string
```

```yml
another_example_item:
  Id: diamond_sword
  NBT:
    Base:
      ATag: 20
      SomeOtherTag: something
    GemSlots:
      RedGem: 0
    Denizen NBT:
      somedenizentag: a_string
```

#### Armor Trim NBT
```yml
another_example_item: 
  Id: iron_chestplate
  NBT: 
    Trim: 
      material: minecraft:iron
      pattern: minecraft:shaper
```

### **ItemVersion**
### **CRUCIBLE ONLY **
Updates the item on MM reload when ItemVersion differs.
This allows you to update items when MM reloads by changing the ItemVersion. If you haven't reset your config.yml in a while, then this feature requires the following to be added to the config.yml:

```yml
ItemUpdating:
  Enabled: true
```

Below are a couple examples:

```yml
yet_another_example_item:
  Id: diamond_sword
  ItemVersion: 1
  Lore:
    - "Really really cool sword."
```

```yml
yet_another_example_item:
  Id: diamond_sword
  ItemVersion: 2
  Lore:
    - "I hated the old lore so I updated it."
```

The second sword will replace the first sword with the updated lore whenever a player interacts with it in their inventory.


### Firework
Sets several firework or firework_charge items.
See [firework](/Items/Firework) for a break-down for each of its options.
```yml
example_item:
  Id: firework
  Firework:
  Colors:
    - 255,0,255
    - 0,0,0
  FadeColors:
    - 200,0,0
  Flicker: true
  Trail: true
```
Examples
--------

More item examples can be found in the [Examples](/examples/Common-Examples#items) section.
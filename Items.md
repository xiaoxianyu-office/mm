Items
=====

![](http://fs5.directupload.net/images/160306/or6m6n2s.jpg)

Making custom items in Mythic Mobs is quite easy.
Unlike mobs and skills however, items made with this plugin do not come with any special or unique options.
Any items you create with MythicMobs could also be created by Minecraft commands,
though making the items using the MythicMobs configurations is much more comfortable.

Of the following options available for items, only `internal_name` and `Id` are required. All other options/attributes are completely optional.

You can make any number of files in the `\plugins\MythicMobs\Items` folder, and they can be
named anything you like as long as the file ends in .yml.

Breaking down the options
-------------------------

#### **Internal_Name**
This string will be how your item is referenced internally in MythicMobs and can be any name you like. 
Must be alphanumeric, **NO SPACES ALLOWED**.
```yml
example_item:
```

#### **Id**
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

#### **Display**
Sets the display name of the item.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
```

#### **Lore**:
Sets the lore of the item. You can generate a random number using `{min-max}`, `<random.#to#>`, or `<random.float.#to#>`.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
  Lore:
    - <rainbow>This line is a rainbow</rainbow>
    - <red>This line should be red</red>
    - 'Tis but a scratch
    - This is a random generated number > <random.-1to50>
```

#### **Model**
Sets the CustomModelData tag on the item.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
  Model: 12345
```

#### **Attributes**
Special field that allows the addition of item attributes to certain armor slots. See [Item Attributes](/Items/Attributes).
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
  Model: 12345
  Attributes:
    Chest:
      Health: 25
```

#### **Amount**
Sets the default amount of items to give when this item is being called by the plugin.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
  Model: 12345
  Attributes:
    Chest:
      Health: 25
  Amount: 1
```

#### **Options**
A special field that comes with numerous sub-options. See [Item Options](/Items/Options).
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Model: 12345
  Attributes:
    Chest:
      Health: 25
  Amount: 1
  Options:
    Color: 255,0,0
    Durability: 0
```

<!-- SEE ITEM OPTIONS
#### **Durability**:
Sets the durability of the item.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
  Model: 12345
  Attributes:
    Chest:
      Health: 25
  Amount: 1
  Options:
    Color: 255,0,0
```
-->

#### **Enchantments**
Any items can have any enchantments(s).
A list of available enchantments can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html).
See also [enchantments](/items/Enchantments) page on how to configure item enchantments.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
  Display: <green>An Example Item</green>
  Model: 12345
  Attributes:
    Chest:
      Health: 25
  Amount: 1
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
  Data: 0
  Display: <green>An Example Item</green>
  Model: 12345
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
Sets the potion effects of the item. These effects won't do anything if the [base item](Items#Id) is not a potion
-   This allows you to add potion effects to your items.
-   These effects won't do anything, except for showing up in the item tooltip, if the specified item isn't a potion.
-   See [Potions](/Items/Potions).

<!-- -->

#### **BannerLayers:**
-   This option allows you to edit the layers of a banner.
-   Won't do anything if the selected item isn't a banner.
-   This option is capable of passing minecraft's 6 layer limit. However, adding excessive amounts of layers may cause weird behavior and will not be supported.
-   See [Banner Layers](/Items/Banner%20Layers)

### **NBT**:
- Specify what NBT tags to put on your items in the format:

```
Item:
  Id: DIAMOND_SWORD
  NBT:
    Base:
      ATag: 20
      SomeOtherTag: something
    GemSlots:
      RedGem: 0
    'Denizen NBT':
      somedenizentag: a_string
```

You can add a prefix to the tag value to change its type, tag values are STRINGS by default.

| Prefix   | Example             |
|----------|---------------------|
| int/     | ATag: int/2         |
| float/   | ATag: float/2.5555  |
| double/  | ATag: double/2.5555 |
| byte/    | ATag: byte/1        |
| bool/    | ATag: bool/false    |
| boolean/ | ATag: boolean/true  |


This allows cross-over with a lot of other plugins, or just for storing
some custom information.

For the more technically-inclined, anything under 'Base' will go under the item's base compound tag, and anything else will go under the corresponding key (or if no sub-items are defined, everything will go under the base tag).

If using with Denizen, all tags you want to use in Denizen must go under 'Denizen NBT' and must be lower-case to work in your Denizen scripts.

Examples
--------

More items can be found in the [Examples](/examples) section.
```yml
ClothSlippers:
  Id: leather_boots
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
```yml
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
  Attributes:
    MainHand:
      Damage: 100
      Health: 123
  Options:
    Color: 200,200,200
    HideFlags: false
    Unbreakable: true
  Enchantments:
  - DURABILITY:1
  - ARROW_FIRE:10
```
This example will hide enchantments and potion effects that are on the
item:
```yml
potato:
  Id: carrot_item
  Enchantments:
  - DURABILITY:5
  PotionEffects:
  - BLINDNESS 20 1
  Hide:
  - ENCHANTS
  - POTION_EFFECTS
```
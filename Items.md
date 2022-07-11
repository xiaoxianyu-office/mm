Items
=====

![](http://fs5.directupload.net/images/160306/or6m6n2s.jpg)

Making custom items in Mythic Mobs is quite easy. Unlike mobs and skills however, items made with this plugin do not come with any special or unique options. Any items you create with MythicMobs could also be created by Minecraft commands, though making the items using the MythicMobs configurations is much more comfortable.

Of the following options available for items, only ```internal_itemname``` and ```Id``` are required. All other options/attributes are completely optional.

You can make any number of files in the `\plugins\MythicMobs\Items` folder, and they can be
named anything you like as long as the file ends in .yml.
```
iternal_itemname:
  Id:
  Data:
  Display:
  Model:
  Attributes:
  Amount:
  Options:
  Durability:
  Enchantments:
  Lore:
  PotionEffects:
  BannerLayers:
```
Breaking down the options
-------------------------

#### **Internal_Name**:
- This string will be how your item is referenced internally in MythicMobs and can be any name you like.
- Must be alphanumeric, **NO SPACES ALLOWED**.
   - Examples:
     -   ```strong_sword:```
     -   ```StrongSword:```
     -   ```strongsword:```
     -   ```StrongSword1:```

<!-- -->

#### **Id**:
-   Defines the type of item.
-   Can be either the item id or the bukkit material/item name.
-   A list of Spigot IDs for the current version is [available here.](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html)
    -   Example:
        -   ```Id: diamond\_sword```
    -   It is STRONGLY RECOMMENDED to use namespaced item IDs, e.g. ```diamond\_sword```
    -   Numbered IDs do not exist in versions 1.13.2 and above, and you will save yourself a lot of time if you don't rely on the old numbered ID system.

<!-- -->

#### **Data**:
-   Sets the data value of the item created.
-   Used to specify the *used up* durability points on items, weapons or armor or to specify the sub-type of a block.

<!-- -->

#### **Display**:
-   Sets the display name of the item.
-   Supports color codes and string variables: [Variables](/skills/stringvariables)
-   Can use hex colors in this format `<#FFFFFF>`
-   Can use gradients using this format `<gradient:#color1:#color2>text</gradient>`
-   Can use rainbow using this format `<rainbow>YOURTEXTHERE</rainbow>`
-   Must be encased by single quotes.
-   For using single quotes inside of the name, you can use the &lt;&sq&gt; variable.
    -   Examples:
        -   ```Display: 'Very Strong Sword'```
        -   ```Display: '&eVery Strong Sword'```
        -   ```Display: 'Phil<&sq>s Strong Sword'```
        -   ```Display: 'Phil''s Strong Sword'```
<!-- -->

#### **Model**:
-   Sets the CustomModelData tag on the item.
-   Only usable in 1.14+
    - Examples:
      - ```Model: 1```

<!-- -->
#### **Attributes**:
-   Special field that allows the addition of item attributes to certain entity slots: [Item Attributes](/Items/Attributes)

<!-- -->

#### **Amount**:
-   Defines the default amount of items to give when this item is being called by the plugin.
    -   Examples:
        -   ```Amount: 8```

<!-- -->

#### **Options**:
-   This is a special field which comes with numerous sub-options, determining lots of extra attributes for the item.
-   A complete list of all available options: [Item Options](/Items/Options)

<!-- -->

#### **Durability**:
-   Defines the starting durability of the item.

<!-- -->

#### **Hide**:
- Special field that allows to hide specific things from the item tooltip. All the possible flags that can be hidden are "ATTRIBUTES", "ENCHANTS", "DESTROYS", "DYE", "PLACED\_ON","POTION\_EFFECTS" and "UNBREAKABLE".

    - Examples
      ```
      Hide:
      - ATTRIBUTES
      - UNBREAKABLE
      ```

<!-- -->

#### **Enchantments**:
-   This field allows to add enchantments to items.
-   Any type of of item can have any enchanment(s).
-   A complete list of all available enchantments: [Enchantments](/Items/Enchantments)

<!-- -->

#### **Lore**:
-   Allows you to add custom lore to your items.
-   Supports color codes and string [Variables](/skills/stringvariables).
-   Can use hex colors in this format `<#FFFFFF>`
-   Can use gradients using this format `<gradient:#color1:#color2>text</gradient>`
-   Can use rainbow using this format `<rainbow>YOURTEXTHERE</rainbow>`
-   Must be encased by single quotes.
-   For using single quotes inside of the name, you can use the &lt;&sq&gt; variable.
-   Putting number ranges surrounded by curly braces will generate a random number in that range when the item is created (i.e. *Health: +{100-200}* would become something like *Health: +152*). Works with ItemLoreStats.
    - Examples:
      ```
       Lore:
       - '&rThe weapon of a true warrior'
       - ''
       - '&cIncreases ones greed'`
      ```
<!-- -->

#### **PotionEffects:**
-   This allows you to add potion effects to your items.
-   These effects won't do anything, except for showing up in the item tooltip, if the specified item isn't a potion.
-   See [Potions](/Items/Potions).

<!-- -->

#### **BannerLayers:**
-   This option allows you to edit the layers of a banner.
-   Won't do anything if the selected item isn't a banner.
-   This option is capable of passing minecraft's 6 layer limit. However adding excessive amounts of layers may cause weird behavior and will not be supported.
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
```
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
```
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
    Damage: 100
    Health: 123
    KnockbackResistance: 1
    MovementSpeed: 0.05
    HideFlags: false
    Unbreakable: true
  Enchantments:
  - DURABILITY:1
  - ARROW_FIRE:10
```
This example will hide which enchantments and potion effects are on the
item:
```
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
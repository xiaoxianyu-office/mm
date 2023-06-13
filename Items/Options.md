All available options will be listed here.
These options must be placed under the `Options:` tag inside your item configurations.
```yml
example_item:
  Id: diamond
  Options:
    SomeOption: value
```

Universal Options
-----------------

These options are applicable to all items:

**Repairable: \[true/false\]**

  - Sets the repair cost of the item to maximum, making it completely uneditable in anvils and/or enchantment tables.
  - Will override the RepairCost option.
  - Defaults to false.

**RepairCost: \[number\]**

  - Sets the repair cost of the item.

**Unbreakable: \[true/false\]**

  - Sets the unbreakable tag on the item.
  - Items with this set to true will not lose durability.

**HideFlags: \[true/false\]**

  - Hides all the item flags, making things like enchants not visible in the item's lore (please note however that the item will still have an enchanted glow).

**PreventStacking: \[true/false\]**

  - Prevents the item from stacking to similar items.

**Model: \[number\]**

  - Sets the custom model data ID for the item

Playerheads
-----------

Only applicable to playerhead type items:

**Player: \[name\]**

  - Sets the texture of the player head.
  - [name] must be the IGN of the target player.
  - Player heads must use data value 3 for this to work.
  - Examples:
    - Player: Herobrine

**SkinTexture: \[url\]**

  - Also sets the texture of the player head, but instead uses a SkinURL.
  - Player heads must use data value 3 for this to work.
  - Type into browser: https://sessionserver.mojang.com/session/minecraft/profile/trimmeduuidofplayerhere
  - Use http://mcuuid.net/ to find the trimmed uuid of the player
  - This option also supports hashes. 
For example:
```yaml
Options:
  SkinTexture: eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvODdlMGFhOTQzM2RiYTliNzU5MzJhMTFkYzk0ZDQwNmJkZTE5ZTg2MzUxNDIxNDkyYjNlZDM3OGM4ZTFhN2NjIn19fQ==
```
Dyeable Items
-------------

**Color: \[R,G,B\] OR \[DyeColor\]**

-   Dyes the armor piece to a color according to Red, Green, Blue
    settings. 0-255
-   Alternately can use a predefined color. Found
    [here](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/DyeColor.html).
-   Can pick colors using the Paint program on Windows. Open it up then choose "Edit Colors" to get your RGB value
-   Only usable on leather armor type and banners.

**Fireworks**
--------------------

* Added options for FIREWORK and FIREWORK_CHARGE items
* For Colors and FadeColors, you can specify what colors you want using the format **RED,GREEN,BLUE**

```yaml
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
========
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
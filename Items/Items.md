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

#### Template
Items can use [Templating](/Mobs/Templates) like mobs, while referencing other items.  
```yaml
MyItem:
  Template: MyOtherItem
```
```yaml
MyOtherItem:
  Template: YetAnotherItem, AndAnotherOne
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

#### MaxDurability
Changes the maximum number of uses an item has. Note: Must be an unstackable item.     
```yaml
example_item:
  Id: diamond_sword
  MaxDurability: 600
```

#### Durability
Sets the amount of durability to take off the item. The below example sets a Diamond Sword to have 1461 durability since by default it has 1561.
```yml
example_item:
  Id: diamond_sword
  Durability: 100
  Display: <green>An Example Item</green>
```

#### Attributes
Special field that allows the addition of item attributes to certain armor slots. See [Item Attributes](/Items/Attributes).
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Attributes:
    Chest:
      Health: 25
```

#### Amount
Sets the default amount of items to give when this item is being called by the plugin.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Amount: 1
```

#### Options
A special field that comes with numerous sub-options. See [Item Options](/Items/Options).
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Options:
    AppendType: true
    Color: 255,0,0
```

#### Enchantments
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

#### Hide
Special field that allows to hide specific things from the item tooltip.
All possible flags can be found:
- [here if you have **Spigot**](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)
- [here if you have **Paper**](https://jd.papermc.io/paper/1.21.3/org/bukkit/inventory/ItemFlag.html) 
> If the server version is <1.20.5, you can also use `HIDE_POTION_EFFECTS`
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

#### PotionEffects
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
| Effects Attributes | Aliases | Description                                                   | Default |
|--------------------|---------|---------------------------------------------------------------|---------|
| duration           | d       | The duration of the effect                                    | 60      |
| level              | l       | the level of the effect. The actual level will be this one +1 | 0       |
| ambientparticles   | ambient, a | Whether ambient particles should be present                | false   |
| hasparticles       | particles, p | Whether particles should be present                      | true    |
| hasicon            | icon, i | Whether the effect icon should be displayed                   | true    |


#### BannerLayers
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

#### CanPlaceOn
Sets what blocks this item can be placed on, if the player is in adventure mode.
```yaml
MyCoolAnvil:
  Id: ANVIL
  CanPlaceOn:
  - diamond_block
```

#### CanBreak
Sets what blocks this item can break, if the player is in adventure mode.
```yaml
MyCoolStick:
  Id: STICK
  CanBreak:
  - grass_block
  - diamond_block
  - obsidian
```

#### BlockStates
Allows you to specify the block states of items
```yaml
TestBlockStates:
  Material: OAK_SLAB
  Display: 'Waterlogged Slab'
  Options:
    Placeable: true # Crucible Option
  BlockStates:
  - type top
  - waterlogged true
```

#### Glider
Allows item to be used as an elytra.  
Used to handle the [glider component](https://minecraft.wiki/w/Data_component_format/glider) of an item.  
```yaml
MyItem:
  Glider: true
```

#### Group
Sets the group the item is in for `/mm items browse`.
```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  Group: 'Armor'
```

#### NBT
Sets what NBT tags to put on your items.
This allows cross-over with a lot of other plugins, or just for storing custom information.

Before you add an NBT tag to your items, you have to know [SNBT formatting](https://minecraft.wiki/NBT_format#SNBT_format).
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

#### Trim
Sets the trim of the item.
```yaml
example_item:
  Material: GOLDEN_CHESTPLATE
  Options:
    Trim:
      Material: iron
      Pattern: wild
```

#### Firework
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

#### Book
Set of options for books
```yaml
SomeBook:
  Id: WRITTEN_BOOK
  Title: <green>How to make YouTube Videos
  Author: CarsonJF
  Pages:
  - "Page 1"
  - "Page 2\n\nwith some other lines"
  - "Page 3"
```

#### AttackRange
Changes the item's attack range. Used to handle the [attack_range component](https://minecraft.wiki/w/Data_component_format/attack_range) of an item.  

```yaml
AMythicItem:
  AttackRange:
    Min: 0
    Max: 4
    MinCreative: 0
    MaxCreative: 5
    HitboxMargin: 0.3
    MobFactor: 1
```

#### Consumable
Allows item to be eaten. Includes customizable animations and sounds.  
Used to handle the [consumable component](https://minecraft.wiki/w/Data_component_format/consumable) of an item.  
```yaml
MyExampleItem:
  Consumable:
    ConsumeSeconds: 3
    HasParticles: false
    Animation: SPEAR
    Sound: item.crossbow.quick_charge_3
    ConsumeEffects:
    # The following are SPECIAL MECHANICS and are the only ones that you can use in this field
    - potion{type=absorption;d=200}
    - randomteleport{radius=5}
    - removePotion{type=wither}
    - clearAllEffects
    - sound{sound=entity.ghast.scream}     
```

#### DeathProtection
If present, this item protects the holder from dying by restoring a single health point, like a Totem of Undying does.  
Used to handle the [death_protection component](https://minecraft.wiki/w/Data_component_format/death_protection) of an item.  
```yaml
MyTotemItem:
  DeathProtection:
    ConsumeEffects: # Same as Consumable's
    - potion{type=absorption;d=200}
    - randomteleport{radius=5}
    - removePotion{type=wither}
    - clearAllEffects
    - sound{sound=entity.ghast.scream}     
```


#### Food
Used to handle the [food component](https://minecraft.wiki/w/Data_component_format/food) of an item.  
Required [Consumable](/Items/Items#consumable) to be set in order to work
```yaml
NetheritePops:
  Material: NETHERITE_SCRAP
  Display: 'Delicious Scraps'
  Food:
    Nutrition: 2
    Saturation: 2
    CanAlwaysEat: true
```


#### Equippable
Used to handle the [equippable item component](https://minecraft.wiki/w/Data_component_format/equippable) of an item 

| Tag               | Description                                                             | Default  |
|-------------------|-------------------------------------------------------------------------|----------|
| Model             | The resource location of the equipment model to use when equipped. If a namespace is not used, it will default to `minecraft:` |          |
| Slot              | The [slot](/Skills/EquipSlot) to put the item on. If not specified, the plugin will try to "guess" it based on whether the base material contains any of the following strings: `_HELMET`, `_CHESTPLATE`, `_LEGGINGS`, `_BOOTS` or `SHIELD` |          |
| CameraOverlay     | The resource location of the overlay texture to use when equipped. If a namespace is not used, it will default to `minecraft:` |          |
| Dispensable       | Whether the item can be dispensed by using a dispenser                  | true     |
| Swappable         | Whether the item can be equipped into the relevant slot by right-clicking | true   |
| DamageOnHurt      | Whether this item is damaged when the wearing entity is damaged           | true   |
| EquipSound        | The sound to play when the item is equipped                               | item.armor.equip_generic |
| EntityTypes       | A list of Entity Types that can equip this item                           |        |

```yaml
KING_HELMET:
  Id: PAPER
  Display: '&dKing Helmet'
  Equippable:
    Model: yourNamespace:thePathToYourCustomModel
    Slot: HEAD
    CameraOverlay: yournamespace:thePathToYourTexture
    Dispensable: true
    Swappable: true
    DamageOnHurt: true
    EquipSound: "item.armor.equip_iron"
    EntityTypes: 
      - "PLAYER"
```

#### UseCooldown
Used to handle the [use_cooldown item component](https://minecraft.wiki/w/Data_component_format/use_cooldown) of an item 

| Tag               | Description                                                             | Default  |
|-------------------|-------------------------------------------------------------------------|----------|
| CooldownGroup     | The unique resource location to identify this cooldown group. If present, the item is included in a cooldown group and no longer shares cooldowns with its base item type, but instead with any other items that are part of the same cooldown group. If a namespace is not used, it will default to `minecraft:` |         |
| CooldownSeconds   | The cooldown duration in seconds. Must be an integer, so the cooldown cannot be defined up to the tick |          |

```yaml
ExampleItem:
  Material: STICK
  UseCooldown:
    CooldownGroup: coolwands # write only in lowercase!
    CooldownSeconds: 3
``` 

#### Tool
Used to handle the [tool item component](https://minecraft.wiki/w/Data_component_format/tool) of an item 

| Tag               | Description                                                             | Default  |
|-------------------|-------------------------------------------------------------------------|----------|
| DamagePerBlock    | The amount of durability to remove each time a block is broken with this tool. Must be a non-negative integer |          |
| DefaultMiningSpeed | The default mining speed of this tool, used if no rule overrides it    | 1.0      |
| Rules             | A list of rules for the tool                                            |          |

| Rule Attributes    | Aliases | Description                                                   | Default |
|--------------------|---------|---------------------------------------------------------------|---------|
| materials          |         | A list of materials for which this rule applies. Can, optionally, also be a single block tag   |         |
| speed              |         | If the material being mined matches, overrides the default mining speed   | 1.0     |
| isCorrectForBlock  |         | If the material being mined matches, overrides whether or not this tool is considered correct to mine at its most efficient speed, and to drop items if the block's loot table requires it | false  | 

```yaml
OBSIDIAN_BREAKER:
  Id: COD
  Display: '&8Obsidian Breaker'
  Tool:
    DamagePerBlock: 1
    DefaultMiningSpeed: 0.0
    Rules:
      - materials: "OBSIDIAN,CRYING_OBSIDIAN"
        speed: 10000.0
        isCorrectForBlock: true
```
```yaml
TREE_BREAKER:
  Id: COD
  Display: '&aTree Breaker'
  Tool:
    DamagePerBlock: 1
    DefaultMiningSpeed: 0.0
    Rules:
      - materials: "completes_find_tree_tutorial" # Example of a Tag being used
        speed: 10000.0
        isCorrectForBlock: true
```

#### TooltipStyle
Used to handle the [tooltip style](https://minecraft.wiki/w/Data_component_format/tooltip_style) of an item.  
The resource location of the custom sprites for the tooltip background and frame which references textures `/assets/<namespace>/textures/gui/sprites/tooltip/<id>_background` and `/assets/<namespace>/textures/gui/sprites/tooltip/<id>_frame`, which can be used with a TooltipStyle's value of <namespace>:<id>

```yaml
ExampleItem:
  Id: STONE_SWORD
  TooltipStyle: minecraft:verycooltooltip
```

#### Spawner
Configure the options for a SPAWNER item
```yaml
TestSpawner:
  Material: SPAWNER
  Display: 'Testing Spawner'
  Spawner:
    Delay: 0
    MinSpawnDelay: 20
    MaxSpawnDelay: 80
    RequiredPlayerRange: 16
    SpawnCount: 4
    SpawnRange: 8
    MaxNearbyEntities: 8
    Mobs:
    - Type: TestingDummy
      Weight: 5
      MinBlockLight: 10
      MaxBlockLight: 10
      MinSkyLight: 10
      MaxSkyLight: 10
```


#### DropOptions
Allows the item to be inherently dropped with specific [FancyDrops Options](/drops/FancyDrops#drop-attributes)

```yaml
LegendarySword:
  Id: DIAMOND_SWORD
  Display: '<red>Legendary Sword'
  DropOptions:
    # Default drop settings for this item
    DropGlowColor: GOLD
    DropBeamColor: '#FFA500' # Orange beam
    DropLootsplosion: true
    DropHologram: true
    DropVFX: true
    DropVFXMaterial: DIAMOND
    DropVFXData: 0
    DropVFXColor: '#55FF55'
    DropBillboarding: CENTER
    DropBrightness: 15
    DropClientSide: false
```

#### Rarity
Sets the rarity of the item.  
Can be COMMON, UNCOMMON, RARE and EPIC
```yaml
TheMusical:
  Rarity: EPIC
  Material: COMPASS
```


## Examples
More item examples can be found in the [Examples](/examples/Common-Examples#items) section.
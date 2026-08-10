![](http://fs5.directupload.net/images/160306/or6m6n2s.jpg)

Making custom items in Mythic Mobs is quite easy. Unlike mobs and skills however, items made with this plugin do not come with any special or unique options. Any items you create with MythicMobs could also be created by Minecraft commands, though making the items using the MythicMobs configurations is much more comfortable.

Of the following options available for items, only `internal_name` and `Id` are required. All other options/attributes are completely optional.

You can make any number of files in the `\plugins\MythicMobs\Items` folder, and they can be named anything you like as long as the file ends in .yml.

## Breaking Down The Item Configuration

#### Internal_Name

This string will be how your item is referenced internally in MythicMobs and can be any name you like. Must be alphanumeric, **NO SPACES ALLOWED**.

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

<!--#### **Data**
Used to specify the *used up* durability points on items.
```yml
example_item:
  Id: leather_chestplate
  Data: 0
```-->

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

#### ItemName
Used to set the [item_name item component](https://minecraft.wiki/w/Data_component_format#item_name).   
Unlike [Display](Items/Items#display), it is not italic, does not count as a custom name for anvil or predicate checks, and suppports the same color formatting as [Display](Items/Items#display). 
```yaml
DirtyDiamond:
  Id: diamond
  ItemName: <#DAA06D>Dirt
```

#### CustomModelData

Sets the CustomModelData component on the item. `Model` is also another alias for `CustomModelData`.

In addition to a regular number, other data types can be specified by prefixing the value with `type/`, similar to [NBT](#nbt). CustomModelData can also be a list.

```yml
example_item:
  Id: leather_chestplate
  Display: <green>An Example Item</green>
  CustomModelData: 5
```

```yml
example_item:
  Id: leather_chestplate
  CustomModelData:
  - float/1,2,3
  - string/something
  - boolean/true
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

Any items can have any enchantments(s). A list of available enchantments can be found [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/enchantments/Enchantment.html). See also [enchantments](/items/Enchantments) page on how to configure item enchantments.

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

Special field that allows to hide specific things from the item tooltip. All possible flags can be found:

- [here if you have **Spigot**](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/ItemFlag.html)
- [here if you have **Paper**](https://jd.papermc.io/paper/1.21.3/org/bukkit/inventory/ItemFlag.html)

> If the server version is \<1.20.5, you can also use `HIDE_POTION_EFFECTS`

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

Sets the potion effects of the item. These effects won't do anything if the [base item](#id) is not a `potion`, `splash_potion`, `lingering_potion`, or `tipped_arrow`. See [Potions](/Items/Potions).

```yml
example_item:
  Id: potion
  Display: <#f99cb3>Pink potion
  Options:
    Color: 249,156,179
  PotionEffects:
    - CONFUSION 100 2
```

| Effects Attributes | Aliases | Description | Default |
|--------------------|---------|-------------|---------|
| duration | d | The duration of the effect | 60 |
| level | l | the level of the effect. The actual level will be this one +1 | 0 |
| ambientparticles | ambient, a | Whether ambient particles should be present | false |
| hasparticles | particles, p | Whether particles should be present | true |
| hasicon | icon, i | Whether the effect icon should be displayed | true |

#### BannerLayers

Sets the banner layers of a banner or a shield. See [Banner Layers](/Items/Banner-Layers).

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

Allows item to be used as an elytra.\
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

Sets what NBT tags to put on your items. This allows cross-over with a lot of other plugins, or just for storing custom information.

Before you add an NBT tag to your items, you have to know [SNBT formatting](https://minecraft.wiki/NBT_format#SNBT_format). A tag value's type can be changed by adding a prefix to the tag value:

| Prefixes | int/ | float/ | double/ | byte/ | bool/ | boolean/ |
|----------|------|--------|---------|-------|-------|----------|

Let's convert this snbt: `{name1:123,name2:"sometext1",name3:{subname1:456,subname2:"sometext2"}}` to mythic formatting:

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

Sets several firework or firework_charge items. See [firework](/Items/Firework) for a break-down for each of its options.

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

Allows item to be eaten. Includes customizable animations and sounds.\
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

If present, this item protects the holder from dying by restoring a single health point, like a Totem of Undying does.\
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

Used to handle the [food component](https://minecraft.wiki/w/Data_component_format/food) of an item.\
Required [Consumable](/Items/Items#consumable) to be set in order to actually consume a non-consumable item.

```yaml
MyThiccApple:
  Material: apple
  Display: 'Red Delicious'
  Food:
    Nutrition: 10
    Saturation: 20
    CanAlwaysEat: false
```

```yaml
NetheritePops:
  Material: NETHERITE_SCRAP
  Display: 'Delicious Scraps'
  Consumable:
    ConsumeSeconds: 0.5
    HasParticles: true
    Animation: EAT
  Food:
    Nutrition: 20
    Saturation: 20
    CanAlwaysEat: true
```

#### Equippable

Used to handle the [equippable item component](https://minecraft.wiki/w/Data_component_format/equippable) of an item

| Tag | Description | Default |
|-----|-------------|---------|
| Model | The resource location of the equipment model to use when equipped. If a namespace is not used, it will default to `minecraft:` |  |
| Slot | The [slot](/Skills/EquipSlot) to put the item on. If not specified, the plugin will try to "guess" it based on whether the base material contains any of the following strings: `_HELMET`, `_CHESTPLATE`, `_LEGGINGS`, `_BOOTS` or `SHIELD` |  |
| CameraOverlay | The resource location of the overlay texture to use when equipped. If a namespace is not used, it will default to `minecraft:` |  |
| Dispensable | Whether the item can be dispensed by using a dispenser | true |
| Swappable | Whether the item can be equipped into the relevant slot by right-clicking | true |
| DamageOnHurt | Whether this item is damaged when the wearing entity is damaged | true |
| EquipSound | The sound to play when the item is equipped | item.armor.equip_generic |
| EntityTypes | A list of Entity Types that can equip this item |  |

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

| Tag | Description | Default |
|-----|-------------|---------|
| CooldownGroup | The unique resource location to identify this cooldown group. If present, the item is included in a cooldown group and no longer shares cooldowns with its base item type, but instead with any other items that are part of the same cooldown group. If a namespace is not used, it will default to `minecraft:` |  |
| CooldownSeconds | The cooldown duration in seconds. Must be an integer, so the cooldown cannot be defined up to the tick |  |

```yaml
ExampleItem:
  Material: STICK
  UseCooldown:
    CooldownGroup: coolwands # write only in lowercase!
    CooldownSeconds: 3
```

#### Tool

Used to handle the [tool item component](https://minecraft.wiki/w/Data_component_format/tool) of an item

| Tag | Description | Default |
|-----|-------------|---------|
| DamagePerBlock | The amount of durability to remove each time a block is broken with this tool. Must be a non-negative integer |  |
| DefaultMiningSpeed | The default mining speed of this tool, used if no rule overrides it | 1.0 |
| Rules | A list of rules for the tool |  |

| Rule Attributes | Description | Default |
|-----------------|-------------|---------|
| materials | A list of materials for which this rule applies. Can, optionally, also be a single block tag |  |
| speed | If the material being mined matches, overrides the default mining speed | 1.0 |
| isCorrectForBlock | If the material being mined matches, overrides whether or not this tool is considered correct to mine at its most efficient speed, and to drop items if the block's loot table requires it | false |

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

Used to handle the [tooltip style](https://minecraft.wiki/w/Data_component_format/tooltip_style) of an item.\
The resource location of the custom sprites for the tooltip background and frame which references textures `/assets/<namespace>/textures/gui/sprites/tooltip/<id>_background` and `/assets/<namespace>/textures/gui/sprites/tooltip/<id>_frame`, which can be used with a TooltipStyle's value of :

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

Sets the rarity of the item.\
Can be COMMON, UNCOMMON, RARE and EPIC

```yaml
TheMusical:
  Rarity: EPIC
  Material: COMPASS
```

#### Repairable

Allows the item to be repaired, if damageable, in an anvil using the specified ingredient. Also repairs equipped items in the body slot of a tamed wolf.

Used to handle the [repairable item component](https://minecraft.wiki/w/Data_component_format#repairable).

```yaml
RepairMe:
  Id: stone_pickaxe
  Repairable:
  - STICK
```

#### PiercingWeapon

Available on Minecraft 1.21.11 and newer. Allows an item's melee attack to pierce targets. `Knockback` controls whether targets are knocked back, while `Dismounts` controls whether hit targets are dismounted.

Used to handle the [piercing_weapon item component](https://minecraft.wiki/w/Data_component_format#piercing_weapon).

```yaml
MyThiccSpear:
  PiercingWeapon:
    Knockback: true
    Dismounts: false
    Sound: item.crossbow.shoot
    HitSound: entity.arrow.hit_player
```

#### KineticWeapon

Available on Minecraft 1.21.11 and newer. Allows the item to perform a kinetic charge attack. Its condition groups control when the attack can damage, knock back, or dismount a target.

Used to handle the [kinetic_weapon item component](https://minecraft.wiki/w/Data_component_format#kinetic_weapon).

| Tag | Description | Default |
|-----|-------------|---------|
| ContactCooldownTicks | The cooldown, in ticks, before the weapon can make contact with a target again | 10 |
| DelayTicks | The delay, in ticks, before the kinetic attack begins | 0 |
| ForwardMovement | The amount of forward movement applied during the attack | 0.0 |
| DamageMultiplier | The multiplier applied to the attack's damage | 1.0 |
| Sound | The sound played when the kinetic attack is used | Optional |
| HitSound | The sound played when the kinetic attack hits a target | Optional |
| DamageConditions | Conditions under which the attack can damage a target |  |
| KnockbackConditions | Conditions under which the attack can knock back a target |  |
| DismountConditions | Conditions under which the attack can dismount a target |  |

`DamageConditions`, `KnockbackConditions`, and `DismountConditions` use the following options:

| Condition Attribute | Description | Default |
|---------------------|-------------|---------|
| MaxDurationTicks | The maximum attack duration, in ticks, during which the condition can apply | Required |
| MinSpeed | The minimum speed required for the condition to apply | 0.0 |
| MinRelativeSpeed | The minimum speed relative to the target required for the condition to apply | 0.0 |

```yaml
MyThiccSpear:
  KineticWeapon:
    ContactCooldownTicks: 10
    DelayTicks: 5
    ForwardMovement: 0.9
    DamageMultiplier: 1.25
    Sound: item.mace.smash_ground
    HitSound: item.mace.smash_air
    DamageConditions:
      MaxDurationTicks: 20
      MinSpeed: 0.6
      MinRelativeSpeed: 0.3
    KnockbackConditions:
      MaxDurationTicks: 10
      MinSpeed: 0.4
      MinRelativeSpeed: 0.2
    DismountConditions:
      MaxDurationTicks: 5
      MinSpeed: 0.2
      MinRelativeSpeed: 0.1
```

#### OminousBottleAmplifier

Sets the amplifier of the Bad Omen effect granted by an ominous bottle.

```yaml
MyThiccOminousBottle:
  Type: OMINOUS_BOTTLE
  OminousBottleAmplifier: 4
```

#### PotDecorations

Sets the items displayed on each face of a decorated pot. This also supports dropping custom sherds.

Used to handle the [pot_decorations item component](https://minecraft.wiki/w/Damage_type).

```yaml
MyThiccPot:
  PotDecorations:
    Back: brick
    Left: arms_up_pottery_sherd
    Right: skull_pottery_sherd
    Front: prize_pottery_sherd
```

#### UseRemainder

Sets the item that remains after this item is used. Only works with Vanilla Items.

```yaml
Item:
  Id: pumpkin_pie
  UseRemainder: sugar
```

#### Weapon

Makes the item act as a weapon. `ItemDamagePerAttack` is the durability lost per attack, and `DisableBlockingForSeconds` is how long a blocking item is disabled when attacked.

Used to handle the [weapon item component](https://minecraft.wiki/w/Data_component_format#weapon).

```yaml
MyThiccWeapon:
  Id: stick
  Weapon:
    ItemDamagePerAttack: 2
    DisableBlockingForSeconds: 0.5
```

#### Enchantability

Sets the item's enchantability value for the enchanting table.

```yaml
MyThiccEnchant:
  Enchantability: 5
```

#### BreakSound

Sets the sound played when the item runs out of durability and breaks.

```yaml
MyThiccBreakSound:
  BreakSound: "minecraft:block.glass.break"
```

#### JukeboxPlayable

Sets the song played when the item is inserted into a jukebox.

Used to handle the [jukebox_playable item component](https://minecraft.wiki/w/Data_component_format#jukebox_playable).

```yaml
MyThiccJukeboxSong:
  Id: fermented_spider_eye  
  JukeboxPlayable: "minecraft:thirteen"
```

#### NoteBlockSound

Sets the sound played by a note block when this item is in a player head placed above it.

Used to handle the [note_block_sound item component](https://minecraft.wiki/w/Data_component_format#note_block_sound).

```yaml
MyThiccNoteHead:
  Id: player_head
  NoteBlockSound: "minecraft:block.note_block.harp"
```

#### BlocksAttacks

Allows the item to block attacks. Damage reduction entries select affected [damage types](https://minecraft.wiki/w/Damage_type) and control the blocked amount and angle. `ItemDamage` controls durability damage taken while blocking.

Used to handle the [blocks_attacks item component](https://minecraft.wiki/w/Data_component_format#blocks_attacks).

| Tag | Description | Default |
|-----|-------------|---------|
| BlockDelaySeconds | The delay, in seconds, before blocking becomes active | 0.0 |
| DisableCooldownScale | Scales the cooldown applied when the item is disabled by an attack. If set to 0, this item can never be disabled by attacks. | 1.0 |
| DamageReductions | A list of rules that control which damage is blocked and by how much | All damage is fully blocked |
| ItemDamage | Controls the durability damage dealt to the blocking item | Required |
| HitBlockSound | The sound played when an attack is successfully blocked | None |
| DisabledSound | The sound played when blocking is disabled | None |
| BypassedBy | A damage type or damage-type tag that bypasses this component | None |

Each entry in `DamageReductions` supports the following options:

| Damage Reduction Attribute | Description | Default |
|----------------------------|-------------|---------|
| Type | A list of [damage types](https://minecraft.wiki/w/Damage_type) to which the rule applies | All damage types |
| Base | A fixed amount used when calculating the blocked damage | Required |
| Factor | A multiplier used when calculating the blocked damage | Required |
| HorizontalBlockingAngle | The horizontal angle, in degrees, within which the attack can be blocked | 90.0 |

`ItemDamage` supports the following options:

| Item Damage Attribute | Description | Default |
|-----------------------|-------------|---------|
| Threshold | The incoming damage threshold used when calculating durability damage | 0.0 |
| Base | A fixed amount used when calculating durability damage | 0.0 |
| Factor | A multiplier used when calculating durability damage | 1.5 |

```yaml
MyThiccShield:
  Id: stick
  BlocksAttacks:
    BlockDelaySeconds: 0
    DisableCooldownScale: 1

    DamageReductions:
    - Type: "#minecraft:is_projectile"
      Base: 0
      Factor: 1
      HorizontalBlockingAngle: 90

    - Type:
      - "minecraft:player_attack"
      - "minecraft:mob_attack"
      Base: 0
      Factor: 0.8
      HorizontalBlockingAngle: 90

    ItemDamage:
      Threshold: 0
      Base: 0
      Factor: 1.5

    HitBlockSound: "minecraft:item.shield.block"
    DisabledSound: "minecraft:item.shield.break"
    BypassedBy: "#minecraft:bypasses_shields"
```

#### UseEffects

Controls what happens while a player is holding right-click to use the item. (1.21.11+)

Used to handle the [use_effects item component](https://minecraft.wiki/w/Data_component_format#use_effects).

```yaml
MyThiccEffect:
  Id: stick
  UseEffects:
    CanSprint: true #Defauts to `false`
    InteracVibrations: false #Defaults to `true`
    SpeedMultiplier: 1.0 #Defaults to `0.2`
```

#### SwingAnimation

Controls the item's attack swing animation. (1.21.11+)

Used to handle the [swing_animation item component](https://minecraft.wiki/w/Data_component_format#swing_animation).

```yaml
MyThiccSwing:
  Id: stick
  SwingAnimation:
    Type: WHACK #Defaults to `WHACK` but `NONE` and `STAB` are also available
    Duration: 12 #Defaults to `6`. Measured in Ticks.
```

#### MinimumAttackCharge

A single value from `0.0` to `1.0`. The item cannot attack until the attack cooldown has rechaged to at least this fraction. Vanilla spears use `1.0`, so they only attack at full charge. (1.21.11+)

Used to handle the [minimum_attack_charge item component](https://minecraft.wiki/w/Data_component_format#minimum_attack_charge)

```yaml
MyThiccCharge:
  Id: stick
  MinimumAttackCharge: 1.0
```

## Examples

More item examples can be found in the [Examples](/examples/Common-Examples#items) section.
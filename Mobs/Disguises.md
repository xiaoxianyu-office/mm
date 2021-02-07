===========

Mob disguises are dependent on the plugins [LibsDisguises ](https://www.spigotmc.org/resources/libs-disguises.81/)and [ProtocolLib](https://www.spigotmc.org/resources/protocollib.1997/). They will not work without either of those plugins.

Also note that some versions work better with others- some versions break mob disguises, other players disguises. You'll have to experiment for yourself- there's no consensus on what works

Also also note that disguises are likely to break if you capitalize the disguise type.

Disguises allow you to make your mob look like a different mob, a block, or even an item! Disguises are great for shaking things up with mobs, allowing you to do things that are otherwise not possible… for example, making a spider that looks like a zombie– a zombie that climbs walls!. The possibilities are huge.

Below is a list of disguise types that can be assigned to a mob using the disguise mob option.

Available Disguises
===========
- arrow
- babyzombievillager
- bat
- blaze
- block - Disguise a mob as (literally) a block
- boat
- cave_spider
- chicken
- cow
- creeper
- donkey
- dropped_item - Disguses a mob as a dropped item.
- egg
- ender_crystal
- ender_dragon
- ender_pearl
- ender_signal
- enderman
- experience_orb
- fireball
- firework
- fishing_hook
- ghast
- giant
- horse
- iron_golem
- item_frame
- leash_hitch
- magma_cube
- minecart
- minecart_chest
- minecart_furnace
- minecart_hopper
- minecart_mob_spawner
- minecart_tnt
- mule
- mushroom_cow
- ocelot
- painting
- pig
- pig_zombie
- player - Disguise a mob as a player!
- polar_bear
- primed_tnt
- rabbit
- sheep
- silverfish
- skeleton
- skeleton_horse
- slime
- small_fireball
- snowball
- snowman
- spider
- splash_potion
- squid
- thrown_exp_bottle
- undead_horse
- villager
- witch
- wither
- wither_skeleton
- wither_skull
- wolf
- zombie
- zombie_villager

### Options

All disguises have certain options available to them. These options go under the Disguises block, and can only be used in conjunction with a disguise (they will not work on their own).

- Disguise.Burning: true - Causes the mob to always appear to be burning
- Disguise.Blocking: true - Causes certain disguises to be stuck in the “blocking” animation.
- Disguise.Invisible: true - Makes the mob permanently invisible
- Disguise.Name: - Sets the disguised entity name
- Disguise.ShowName: true - Displays a nametag over certain disguises that would not normally have one (such as a block or item)
- Disguise.Sneaking: true - Causes certain disguises to be stuck in the “sneaking” animation.
- Disguise.Sprinting: true - Causes certain disguises to be stuck in the “sprinting” animation.
- Disguise.ModifyBoundingBox: false - Setting this to false will make mobs keep their original hitbox.
- Disguise.Glowing: [true/false] - Makes the disguise glow permanently.
- Disguise.Gliding: [true/false] - Makes the disguise glide permanently.

“Glowing” and “Gliding” were added in version 2.3.2.

Excessive Example:
```
SneakyDisguisingMob:
  Type: wither_skeleton
  Display: 'meh'
  CustomKillMessages:
  - '<target.name> was sneaked upon! (to death)'
  Health: 128
  Disguise:
    Type: player
    Skin: 'meeeh'
    Player: Steve
    Burning: true
    Blocking: true
    Invisible: false
    ShowName: false
    Sneaking: true
    Sprinting: true
    ModifyBoundingBox: false
```

#### Nameplates

Added in 4.1
Nameplates allow you to extend the nameplates of Player-disguise mobs, which are normally limited to 16 characters.
To use this, simply have Holograms installed and then leave out the “Player” field in your disguise (skin is still required!).
If you don't specify the player field, it will use the Display field instead using a custom nameplate.

```
Monkey:
  Type: skeleton
  Display: "this display name is too long for players normally"
  Disguise:
    Type: player
    Skin: Kurdie
```
This feature requires LibsDisguises and the Holograms plugin: [https://www.spigotmc.org/resources/holograms.4924/](https://www.spigotmc.org/resources/holograms.4924/)

#### Examples

Examples of Disguises being used:

```
MobType: skeleton
Disguise:
  Type: player
  Player: '&8Not Darkitect'
  Skin: Darkitect
```
```
MobType: skeleton
Health: 20
Disguise:
  Type: player
  Player: Ashijin
  Skin: Notch
```
```
MobType: skeleton
Health: 20
Disguise:
  Type: pig
```

------------------------------------------------------------------------

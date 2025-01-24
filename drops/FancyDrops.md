Have you ever thought that drops were a bit *too* plain? Did you want them to sparkle a bit more? Do not worry then: this page documents how that can be done!

But remember! Fancy Drops are only available for **Mythic, [MMOItems](/drops/Drops#drop-types), [Droptables](/drops/DropTables) or Vanilla items**!

[[_TOC_]]

## Drop Options
This is an additional field on the mob config, `DropOptions`, that allows you to determine various behaviors regarding the drops.

```yaml
  DropOptions:
    DropMethod: FANCY
    ShowDeathChatMessage: false
    ShowDeathHologram: false
    PerPlayerDrops: false
    ClientSideDrops: false
    Lootsplosion: false
    HologramItemNames: false
    ItemGlowByDefault: false
    ItemBeamByDefault: false
    ItemVFXByDefault: false
    ItemVFX:
      Material: STONE
      Model: 0
    RequiredDamagePercent: 1
    HologramTimeout: 6000
    HologramMessage:
    - ...
    - ...
    ChatMessage:
    - ...
    - ...
```

### DropMethod
Can be one of two values:
- `VANILLA`, which keeps all of the "normal" drop behaviors  
- `FANCY`, which enables damage tracking, scoreboards and more advanced drop effects. Drops can also be rolled for every participant instead of only once if the relevant config is set to allow it.

So, in essence, this must be set to `FANCY` in order for the rest of the page to work  
Defaults to `VANILLA`  
```yaml
  DropOptions:
    DropMethod: FANCY
```


### ShowDeathChatMessage
Whether to show the death chat message to the players.  
Defaults to `false`.  
```yaml
  DropOptions:
    ShowDeathChatMessage: true
```


### ShowDeathHologram
Whether to show the death hologram to the players.  
Defaults to `false`.  
```yaml
  DropOptions:
    ShowDeathHologram: true
```


### PerPlayerDrops
Whether to calculate the drops of the mob separately for each player involved. Essentially, the drops will be rolled one time for each player.  
> **This is a [Paper-Only] feature!**
```yaml
  DropOptions:
    PerPlayerDrops: true
```


### ClientSideDrops
Whether drops should be seen per-player, in a client side manner. In essence, with this enabled, every player will only be able to see the loot that they themselves gained.
```yaml
  DropOptions:
    ClientSideDrops: false
```


### Lootsplosion
Whether the drops should do a lootsplosion effect by default.  
```yaml
  DropOptions:
    Lootsplosion: true
```


### HologramItemNames
Whether the items should have a hologram name to display them by default.  
```yaml
  DropOptions:
    HologramItemNames: true
```


### ItemGlowByDefault
Whether items should glow by default.  
Using this option seems to add an NBT to the dropped items that makes them unstackable with other items not obtained this way.  
```yaml
  DropOptions:
    ItemGlowByDefault: true
```


### ItemBeamByDefault
Whether items should have a beam by default.  
```yaml
  DropOptions:
    ItemBeamByDefault: true
```


### ItemVFXByDefault
Whether items should have a vfx by default.  
```yaml
  DropOptions:
    ItemVFXByDefault: true
```


### ItemVFX
Options regarding the default VFX of the items
```yaml
  DropOptions:
    ItemVFX:
      Material: STONE # The default material of the vfx
      Model: 0 # The default model of the vfx
```


### RequiredDamagePercent
The required amount of damage to inflict on the mob, quantified as percent of its health, in order for the drops to be generated for the specific player.  
```yaml
  DropOptions:
    RequiredDamagePercent: 1
```


### HologramTimeout
The amount of time after which the hologram that spawns when the mob dies should disappear  
Defaults to `6000`  
```yaml
  DropOptions:
    HologramTimeout: 6000
```


### HologramMessage
What the hologram that spawns when the mob dies should say. Is able to use specific placeholders.
```yaml
  DropOptions:
    HologramMessage:
    - '<#FF9B00>========================'
    - '<mob.name> - <mob.hp>HP'
    - ''
    - '<#FFA300>1st Place | <1.name> | <1.damage>'
    - '<#D1FFFF>2nd Place | <2.name> | <2.damage>'
    - '<#D1FFFF>3rd Place | <3.name> | <3.damage>'
    - '<#E57A00>4th Place | <4.name> | <4.damage>'
    - '<#E57A00>5th Place | <5.name> | <5.damage>'
    - ''
    - 'Your rank: #<player.rank> | <player.damage>'
    - '<#FF9B00>========================'
```
> If there is no player at a specified rank (for instance, if a mob was killed by less than 5 players) then the line where the placeholder is used will not be shown


### ChatMessage
What the message send to the players when the mob dies should say. Is able to use specific placeholders.
```yaml
  DropOptions:
    ChatMessage:
    - '<#F28800>===================================='
    - '<#FFA300>BOSS DEFEATED!'
    - '<#F2B600><mob.name>'
    - ''
    - '<#ffe259>1st Place »<#ffe259> <1.name> - <1.damage>'
    - '<#D1FFFF>2nd Place »<#D1FFFF> <2.name> - <2.damage>'
    - '<#D1FFFF>3rd Place »<#D1FFFF> <3.name> - <3.damage>'
    - '<#E57A00>4th Place »<#E57A00> <4.name> - <4.damage>'
    - '<#E57A00>5th Place »<#E57A00> <5.name> - <5.damage>'
    - ''
    - '<#F2B600>Your rank: #<player.rank> - <player.damage> (<pity> Pity)'
    - '<#F28800>===================================='
```
> If there is no player at a specified rank (for instance, if a mob was killed by less than 5 players) then the line where the placeholder is used will not be shown



## Drop Attributes
Other than the options written above, you can also determine specific behaviors for each drop of the mob, by writing them as inline attributes

```yaml
  Drops:
  - amber_1{itemglow=true;itemglowcolor=GOLD;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
```

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| lootsplosion | lootsplosionenabled, ls | Whether the drop should move outwards once generated        | |
| clientsidedrops | clientsidedropsenabled, csd | Whether the drop should be client side               | |
| hologramname | hologramnameenabled, hn | Whether the drop should have a hologram displaying its name | |
| itemglow  | itemglowenabled, ig | Whether the drop should glow                                       | |
| itemglowcolor | glowcolor, gc | The color of the glow, if set                                        | |
| itembeam  | itembeamenabled, ib | Whether the drop should generate a particle beam above itself      | |
| itembeamcolor | beamcolor, bc | The color of the beam, if set                                        | |
| itemvfx   | ivfx, vfx | Whether the drop should have a item vfx                                      | |
| vfxmaterial | vfxmat, vfxm | The material of the vfx                                                 | |
| vfxdata   | vfxd      | The data of the vfx                                                  | 0       |
| vfxmodel   | vfxitemmodel | The item model of the vfx. Minecraft 1.21.3+                             | |
| vfxcolor  | vfxc, color | The color of the vfx                                                       | |
| pityModifier | pitymod, pmod | The modifier of the pity                                      | 0.0     |
| resetpity | resetp, rp | Whether the pity should be reset                                    | false   |
| pcategory | pitycategory, category | The category of the pity                                | DEFAULT |
| damage    | mindamage, min | The minimum amount of damage that must have been inflicted on the mob in order for this drop to be able to be generated for the player                                  | 0.0     |
| top       | placement, required | The placement in the damage leaderboard required for this drop to be generated for the player                                                                    | 2147483647 |
| billboarding | billboard, bill | The [billboarding] of the hologram                         | VERTICAL |
| brightness | bright, b | The brightness of the hologram                                      | 0       |
| fortune   | | Whether this drop should be affected by the fortune enchant                    | false   |
| fortuneMod | | How much each level of the fortune enchant impact the drop amount             |         |


### Fortune
Fortune drop amount calculation:
```math
  amount = min(1, floor(<random.float.0to1> * (2 + fortuneLevel) * fortuneMod ) ) * amount
```

### Example
```yaml
  Drops:
  - amber_1{itemglow=true;itemglowcolor=GOLD;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - adamantium_ore{itemglow=true;itemglowcolor=WHITE;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - amethyst_1{itemglow=true;itemglowcolor=YELLOW;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - andesite_bricks{itemglow=true;itemglowcolor=LIGHT_PURPLE;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - bananarang{itemglow=true;itemglowcolor=RED;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - augment_sword_midas_6{itemglow=true;itemglowcolor=AQUA;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - blue_stained_tiles{itemglow=true;itemglowcolor=GREEN;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - black_stained_tiles{itemglow=true;itemglowcolor=BLUE;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxdata=21;vfxc=#55ff55} 1 1
  - bismuth_2{itemglow=true;itemglowcolor=DARK_RED;hn=true;lootsplosion=true;vfxmaterial=POTION;vfxmodel="mythic:effects/item_beam_3"} 1 1
```

<!-- LINKS -->
[billboarding]: https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/Display.Billboard.html
[Paper-Only]: https://papermc.io/downloads/all
The BossBar feature is used to give your custom mobs a healthbar in the same style used by the Ender Dragon and Wither, but with a lot more options for customization.

## Syntax

```yaml
internal_mobname:
  Type: <mobtype>
  BossBar:
    Enabled: [true/false]
    Title: '[name]'
    Range: [range]
    Color: [color]
    Style: [style]
    CreateFog: [true/false]
    DarkenSky: [true/false]
    PlayMusic: [true/false]
```

### Color
Available colors for Color (case sensitive): PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE.

### Style
Available styles for Style (case sensitive): SOLID, SEGMENTED_6, SEGMENTED_10, SEGMENTED_12, SEGMENTED_20.

### Range
Range is the distance the BossBar will be displayed to players around the mob.

### Extra Options
CreateFog adds a fog-like effect to the player's vision while in the radius defined for the bossbar.

DarkenSky darkens the sky while in the radius defined for the bossbar, similar to the effect created when the Wither is spawned.

<!--
I'm not too sure what PlayMusic does, but I presume it plays boss music while in the radius defined for the bossbar.
-->


## Examples
```yaml
SuperCreeper:
  Type: creeper
  Display: '&cTest'
  Health: 20
  BossBar:
    Enabled: true
    Title: 'Test'
    Range: 20
    Color: RED
    Style: SOLID
```
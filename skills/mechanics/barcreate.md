## Description
Creates a custom boss bar on the casting mob (cannot be player).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name      | n         | The name of the bossbar.                                             | infobar |
| display   | d, bartimerdisplay, bartimertext | The text displayed on the bar            | <caster.name> |
| value     | v         | How filled the bossbar is. Must be between 0.0 and 1.0.              | 1.0     |
| color     | c, bartimercolor | The [Color](/Mobs/BossBar#color) of the bossbar               | RED<!--type:BarColor--> |
| style     | s, bartimerstyle | The [Style](/Mobs/BossBar#style) of the bossbar               | SOLID<!--type:BarStyle--> |

  

## Examples
```yaml
  Skills:
  - barCreate{
    name="MyBossBar";
    display="<caster.name> - <caster.hp>";
    value=1.0;color=BLUE;
    style=SEGMENTED_6
    } @self ~onSpawn
```


## Aliases
- [x] barAdd
- [x] createBar


<!--TAGS-->
<!--tag:BossBar-->
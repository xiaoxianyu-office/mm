## Description
Modifies a custom boss bar on the casting mob (cannot be player).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name      | n         | The name of the bossbar to modify/set                                | infobar |
| display   | d, bartimerdisplay, bartimertext | The text displayed on the bar           | <caster.name> |
| value     | v         | How filled the bossbar is. Must be between 0.0 and 1.0.              | 1.0     |
| color     | c, bartimercolor | The [Color](/Mobs/BossBar#color) of the bossbar               | RED<!--type:BarColor--> |
| style     | s, bartimerstyle | The [Style](/Mobs/BossBar#style) of the bossbar               | SOLID<!--type:BarStyle--> |


## Examples
```yaml
  Skills:
  - barSet{
    name="MyBossBar";
    display="<caster.name> - <caster.hp>";
    value=1.0;
    color=RED;
    style=SEGMENTED_6
    } @self ~onDamaged
```


<!--TAGS-->
<!--tag:BossBar-->
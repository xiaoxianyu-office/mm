## Description
Removes a custom boss bar on the casting mob (cannot be player).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| name      | n         | The name of the bossbar to remove                                    | infobar |


## Examples
```yaml
  Skills:
  - barRemove{name="MyBossBar"} @self ~onInteract
```


<!--TAGS-->
<!--tag:BossBar-->
## Description
\*\***This is a Premium only feature**\*\*<br>
Causes the mob to stop doing anything based on provided conditions.

**It seems conditions are reversed when using this, for example `day true` will make the mob doNothing if it is night time, and `day false` will make the mob doNothing if its day time.**

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| conditions | c, cond, fleeconditions | The conditions to use                                 |         |


## Examples
This would cause the mob to stop it's AI if the [day](https://git.mythiccraft.io/mythiccraft/MythicMobs/-/wikis/skills/conditions/day) condition is met.
```yaml
ExampleMob:
  Type: ZOMBIE
  AIGoalSelectors:
    - clear
    - doNothing{conditions=[ - day true ]}
```


## Aliases
- [x] nothing
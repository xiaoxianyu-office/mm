## Description
Replaces blocks in a region using WorldEdit. Needs a [@region](/Skills/Targeters/Region) or similar targeter

> **This is a [Premium-Only] mechanic!**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| from      | f | The material to replace                                      | AIR<!--type:MATERIAL--> |
| to        | t | The material to set in place of the replaced one             | AIR<!--type:MATERIAL--> |


## Examples
```yaml
  Skills:
  - worldEditReplace{from=STONE;to=AIR} @Region{min=0,0,0;max=100,100,100;world=resources}
```


## Aliases
- [x] weReplace


<!-- LINKS -->
[Premium-Only]: Premium-Features


<!--TAGS-->
<!--tag:Premium-Only-->
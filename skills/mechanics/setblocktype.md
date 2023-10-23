## Description
Change blocktype at target location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m         | The material for the block to be set to                              | [DIRT](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html "CLICK ME to view valid block materials")                                                                                              |
| data      | md        | Material data value                                                  | 0       |


## Examples
Sets a block at the location of the caster
```yaml
SetBlockExample:
  Skills:
  - setblock{m=STONE;md=0} @selflocation
```
##
Sets a mmoitems block at the location of the target
```yaml
SetMMOItemsBlock:
  Skills:
  - setblock{m=mmoitems:50} @targetlocation
```
##
Sets a block with specified blockstates at the location of the target
```yaml
SetButton:
 Skills:
 - setblock{m=JUNGLE_BUTTON[facing=east,face=floor]} @targetlocation
```
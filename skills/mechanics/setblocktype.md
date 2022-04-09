Mechanic: Set Block Type
========================

Change blocktype at target location.

Attributes
----------

| Attribute | Aliases | Description                    | Default Value |
|-----------|---------|--------------------------------|---------------|
| material  | m       | The material for the block to be set to | [DIRT](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html "CLICK ME to view valid block materials")          |
| data      | md      | Material data value.           | 0             |

As of build 4018/4019 you can now setblock mmoitems custom blocks. An example is below. It would set the targetlocation to the mmoitems block with the id of 50.

As of build 4088 it now supports all blockstates. An example of setting a button on the floor is below. 


Examples
--------

    SetBlockExample:
      Skills:
      - setblock{m=STONE;md=0} @selflocation

    SetMMOItemsBlock:
      Skills:
      - setblock{m=mmoitems:50} @targetlocation

    SetButton:
      Skills:
      - setblock{m=JUNGLE_BUTTON[facing=east,face=floor]} @targetlocation
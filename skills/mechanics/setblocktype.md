Mechanic: Set Block Type
========================

Change blocktype at target location.

Attributes
----------

| Attribute | Aliases | Description                    | Default Value |
|-----------|---------|--------------------------------|---------------|
| material  | m       | The material for the block to be set to | [DIRT](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html "CLICK ME to view valid block materials")          |
| data      | md      | Material data value.           | 0             |
| age       | a     | Sets the age of ageable blocks. If applied to sapplings, it instead sets the growth stage of the sappling. | 0 |
| waterlogged | | Whether or not the block is inside water | false |
| blockface  | bf | Where the block is facing | [NORTH](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/BlockFace.html "CLICK ME to view valid BlockFaces") |
| attachedface | af | Where the buttons or levers are attached. Can be attached to a wall, floor, or ceiling. Used in conjuction with blockface. | [WALL](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/data/FaceAttachable.AttachedFace.html "CLICK ME to view valid faces")|
| axis | | This is not to be confused with blockface. "X" orients the block east-west, "Y" orients the block vertically, and "Z" orients the block north-south.   | Y |
| bisectedhalf | bhalf |  | [TOP](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/data/Bisected.Half.html "CLICK ME to view valid values") |
| slabtype | sb |  | [BOTTOM](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/data/type/Slab.Type.html "CLICK ME to view valid types") |
| stairshape | shape | The shape of the stair block | [STRAIGHT](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/block/data/type/Stairs.Shape.html "CLICK ME to view valid shapes") |

As of build 4018/4019 you can now setblock mmoitems custom blocks. An example is below. It would set the targetlocation to the mmoitems block with the id of 50. The following attributes: age, attachedface, axis, blockface, slabtype, stairshape, waterlogged,  will be ignored when using MMOITEM blocks.

  

Examples
--------

    SetBlockExample:
      Skills:
      - setblock{m=STONE;md=0} @selflocation

    SetMMOItemsBlock:
      Skills:
      - setblock{m=mmoitems:50} @targetlocation
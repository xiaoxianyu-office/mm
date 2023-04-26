Mechanic: fawePaste
===============

Pastes a Schematic using the FAWE Plugin found here: [FAWE](https://www.spigotmc.org/resources/fast-async-worldedit.13932/)

You must create a `Schematics` folder in your MythicMob directory and put the schematics you will use inside that folder.<br>
If the schematic defined in the mechanic is not found inside mm's `Schematics` folder, FAWE's and WE's will be then checked for its presence

Attributes
----------

| Attribute | Aliases | Description                                                   | Default Value |
|-----------|---------|---------------------------------------------------------------|---------------|
| schematic |  s       | Which schematic to load. |               |
| pasteAir | air,a       | Should air be pasted? |               |
| xOffset | x,xo      | The X offset of pasting the Schematic from the target.   | 0             |
| yOffset | y,yo      | The Y offset of pasting the Schematic from the target.   | 0             |
| zOffset | z,zo      | The Z offset of pasting the Schematic from the target.   | 0             |
| chestDropTable | chests,cdt      | Which MythicMob Drop Tables to supply the chests within the Schematic with.   | ""             |
| trappedchestDropTable | trapchests,tcdt      | Which MythicMob Drop Tables to supply the Trapped Chests within the Schematic with.   | ""             |
| blocksPerTick  |    | The number of blocks that are placed every tick          |               |
| pasteID   | pid, id | The paste's id. Can be used to undo the paste via the [undoPaste] mechanic |   |
  

Examples
--------
```yaml
  - fawePaste{schematic=deserttempleiron.schem;y=6;air=true;chestDropTable=IronDropTable} @origin
```


  [undoPaste]: /Skills/mechanics/undopaste
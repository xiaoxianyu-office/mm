Mechanic: Give Item
===================

Gives an item to the target. Supports Droptables.

Attributes
----------

| Attribute   | Aliases | Description       | Default Value |
|-------------|---------|-------------------|---------------|
| item        | i       | The item material (supports for MythicMobs' [Items](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Items/Items) and [Droptables](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/drops/Drops#drop-tables)) |               |
| fakeLooting | fl      | Plays the pickup-item animation from the origin | false |

------------

**Note:**

This mechanic do nothing when targeted target's have no space in its inventory.  

fakeLooting was added in 4.12 MM and it makes the item being given show up on the screen and fly toward the players inventory like when a player picks an item up off of the ground.

  

Examples
--------

    Skills:
    - giveitem{i=diamond_sword} @PIR{r=20} ~onSpawn
    - ...
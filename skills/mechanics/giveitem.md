Mechanic: Give Item
===================

Gives an item to the target

Attributes
----------

| Attribute   | Aliases | Description       | Default Value |
|-------------|---------|-------------------|---------------|
| item        | i       | The item material |               |
| amount      | a       | The amount given  | 1             |
| fakeLooting |         | plays the pickup-item animation from the origin | false |

------------

Note:

fakeLooting was added in 4.12 MM and it makes the item being given show up on the screen and fly toward the players inventory like when a player picks an item up off of the ground. 

  

Examples
--------

    Skills:
    - giveitem{i=diamond_sword;a=1} @PIR{r=20} ~onSpawn
    - ...

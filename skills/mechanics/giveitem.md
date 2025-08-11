## Description
Gives an item to the target. Supports Droptables.  

This mechanic do nothing when targeted target's have no space in its inventory.  

fakeLooting was added in 4.12 MM and it makes the item being given show up on the screen and fly toward the players inventory like when a player picks an item up off of the ground.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | items, i, type, t, material, mat, m | The item material (supports for MythicMobs' [Items](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/Items/Items) and [Droptables](https://git.lumine.io/mythiccraft/MythicMobs/-/wikis/drops/Drops#drop-tables)) You can specify an amount by putting a space and a number after the item name                | <!--type:Item-->|
| fakeLooting | dofakelooting, fl | Plays the pickup-item animation from the origin            | false   |
| variable  | var       | The Item variable whose value is to be given as an actual item                 |


## Examples
```yaml
  Skills:
  - giveitem{i=diamond_sword} @PIR{r=20} ~onSpawn
  - ...
```
The below example would give the players 6 cookies.
```yaml
  Skills:
  - giveitem{i=cookie 6} @PIR{r=20} ~onSpawn
  - ...
```


## Aliases
- [x] give
- [x] giveitems
- [x] itemgive


<!--TAGS-->
<!--tag:Inventory-->
<!--tag:Item-->
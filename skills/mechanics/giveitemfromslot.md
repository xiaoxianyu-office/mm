Mechanic: Give Item From Slot
===================

Gives an item to the target from the item in the given slot of caster.  

Won't consume the item in the given slot of caster)

Attributes
----------

| Attribute   | Aliases | Description       | Default Value |
|-------------|---------|-------------------|---------------|
| slot        | s       | The given slot | None |
| fakeLooting | fl      | plays the pickup-item animation from the origin | false |

**Valid Slots:**

| HEAD | CHEST | LEGS | FEET | HAND | OFFHAND |       
| ---- | ----- | ---- | ---- | ---- | ------- |  
---

Added in MM 4.13

------------

**Note:**

this mechanic do nothing when targeted target's have no space in its inventory.  

fakeLooting was added in 4.12 MM and it makes the item being given show up on the screen and fly toward the players inventory like when a player picks an item up off of the ground.

  

Examples
--------

    Skills:
    - giveitemfromslot{slot=HAND;fakelooting=true} @server ~onTimer:10

Give caster's main handing item to all players on the server.
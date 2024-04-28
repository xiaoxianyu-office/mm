MythicMobs has [a lot of commands]. While all of them are useful in their own right, you might want to know about the more useful ones before diving in, and this guide is here for that exact purpose!

# Reload the plugin
`/mm reload`  
Without reloading, all the changes you may do will not be applied!

# Essentials
### Spawn a mob
`/mm mobs spawn [mobtype]`  
Allows you to spawn the specified mob
### Remove a mob
`/mm mobs kill [mobtype]` To kill the specified mobtype  
`/mm mobs killall` to kill all non persistent mobs  
`/mm mobs killall <radius>` to kill all non persistent mobs in a radius  
### Get an item
`/mm items get [itemname]`  
To get the specified item

# Utility
### Debug Level
`/mm debug [level]`  
Ahhhh, the one and only debug command! It allows for more information regarding mechanics and events that are being executed to be printed out in console, based on the level argument passed to it (using `/mm debug 4` will enable debug message "up to level 4" to be displayed, while `/mm debug 0` will disable all debug messages)
### Listactive
`/mm mobs listactive <mobtype>`  
Allows you to list all the active mobs, optionally filtered by their mobtype, and to obtain further information for their entry, teleport to them or kill/remove them
### Get Coordinates
`/mm utilities getcoordinates`  
Allows you to get formatted coordinates of your position and the one pointed and the target's
### Get Item Info
`/mm utilities getiteminfo`  
Allows you to see all of the nbts present on the held item
### Get Path
`/mm utilities getpathstring`  
With this command you can place blocks and obtain a list of coordinates you can use in patrol aigoal or similar instances
### List All Entities
`mm utilities listallentities <radius/mobtype>`  
Allows you to list all entities, enabling you to filter them by the distance or their type

**[>> Step 5](/Guides/(Step-5)-Extra-Notes)**
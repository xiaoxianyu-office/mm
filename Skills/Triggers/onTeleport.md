## Description
Executes the skill when the mob teleports.  
> There is no associated [@trigger](/Skills/Targeters/Trigger)


## Examples
```yml
EXAMPLE_MOB:
  Type: ENDERMAN
  Skills:
    # sends a message to all the players in the world
    # when the mob teleports
    - message{m=TELEPORT} @World ~onTeleport
```
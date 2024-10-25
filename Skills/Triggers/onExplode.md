## Description
Executes the skill when the mob explodes.  
`mobGriefing` gamerule must be set to true for this to work.  
Generally, this trigger only works with creepers and TNTs since they are the only mobs to actually explode  
> There is no associated [@trigger](/Skills/Targeters/Trigger)


## Examples
```yml
EXAMPLE_MOB:
  Type: CREEPER
  Skills:
    # sends a message to all the players in the world
    # when the mob explodes
    - message{m=EXPLODE} @World ~onExplode
```
## Description
Executes the skill when the mob kills a player.  
> The associated [@trigger](/Skills/Targeters/Trigger) is the player that has been killed


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob kills a player
    - message{m=PLAYER KILLED} @World ~onPlayerKill
```


## Aliases
- [x] onKillPlayer
## Description
Executes the skill when the player tames the mob.  

> The associated [@trigger](/Skills/Targeters/Trigger) is the player that tamed the mob


## Examples
```yml
EXAMPLE_MOB:
  Type: WOLF
  Skills:
    # sends a message to all the players in the world
    # when a player tames the mob
    - message{m=I GOT TAMED} @World ~onTame
```
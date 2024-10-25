## Description
Executes the skill when the villager trades with a player.  

> The associated [@trigger](/Skills/Targeters/Trigger) is the player that traded with the villager


## Examples
```yml
EXAMPLE_MOB:
  Type: VILLAGER
  Skills:
    # sends a message to all the players in the world
    # when the mob's target changes
    - message{m=TRADED} @World ~onTrade
```
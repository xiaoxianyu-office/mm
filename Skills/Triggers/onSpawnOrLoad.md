## Description
Executes the skill when either [~onSpawn](/Skills/Triggers/onSpawn) or [~onLoad](/Skills/Triggers/onLoad) would trigger.


## Examples
```yml
EXAMPLE_MOB:
  Type: VILLAGER
  Skills:
    # sends a message to all the players in the world
    # when the mob spawns or when the mob is loaded after a server restart
    - message{m=SPAWNED! Or was i loaded?} @World ~onSpawnOrLoad
```
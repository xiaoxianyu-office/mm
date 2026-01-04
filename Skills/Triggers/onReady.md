## Description
Executes the skill when the mob is ready to spawn from a [spawner](/Spawners)


## Examples
```yml
EXAMPLE_MOB:
  Type: VILLAGER
  Skills:
    # sends a message to all the players in the world
    # when the mob is about to spawn from a spawner
    - message{m=READY TO SPAWN FROM A SPAWNER} @World ~onReady
    - message{m=READY TO SPAWN FROM A SPAWNER} @World ~onFirstSpawn
```


## Aliases
- [x] onFirstSpawn
## Description
Executes the skill when a player dismounts the mob.

## Examples
```yml
EXAMPLE_MOB:
  Type: HORSE
  Skills:
    # sends a message to the player that dismounted the entity, and prevents it from dismounting entirely with a chance
    - skill{s=[
      - cancelevent
      - message{m=Going somewhere?} @trigger
     ];sync=true} @self ~onDismount 0.7

```


## Aliases
- [x] onUnmount
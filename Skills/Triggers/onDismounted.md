## Description
Executes the skill when the mob is dismounted from.

## Examples
```yml
EXAMPLE_MOB:
  Type: HORSE
  Skills:
    # sends a message to the player that dismounted the entity, and prevents it from dismounting entirely with a chance
    - skill{s=[
      - cancelevent
      - message{m=Going somewhere?} @trigger
     ];sync=true} @self ~onDismounted 0.7

```


## Aliases
- [x] onUnmounted
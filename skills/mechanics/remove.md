## Description
Removes the targeted entity from existence. Does not work on players.

## Attributes
> *This mechanic has no attributes*

## Examples
This mob would despawn 10 seconds after spawning:
```yaml
  Skills:
  - remove{delay=200} @self ~onSpawn
```
This skill despawns the mob immediately when it is right clicked.
```yaml
  Skills:
  - remove @self ~onInteract
```


<!--TAGS-->
<!--tag:Meta-->

## Description
Activates a MythicMobs [spawner](Spawners), causing it to spawn mobs. Will not
override any conditions or options set on the spawner.

>Best used in conjunction with setting the `useTimer` attribute on
spawners to `false`.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| spawners  | spawner, s| The name of the spawner(s) to activate. This can accept groups and wildcards also using the appropriate syntax                                                              | NONE    |


## Examples
This would activate the spawner named "BossAdd"
```yaml
    Skills:
    - activatespawner{spawner=BossAdd}
```
##
This example would activate all spawners in the group "Castle"
```yaml
    Skills:
    - activatespawner{spawner=g:Castle}
```
##
This example would activate all spawners starting with
"DungeonBoss1Spawner" (i.e. DungeonBoss1Spawner1, DungeonBoss1Spawner2,
etc)
```yaml
    Skills:
    - activatespawner{spawner=DungeonBoss1Spawner*}
    - ...
```


## Aliases
- [x] as
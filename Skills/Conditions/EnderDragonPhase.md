## Description
Checks the phase of the target Ender Dragon entity.  
A list of valid phases can be found in the [Spigot Phase javadoc](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EnderDragon.Phase.html).


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| phase     | p         | A list of phases to match                                            |         |


## Examples
```yaml
  Conditions:
  - enderdragonphase{phase=CIRCLING} true
```
```yaml
Conditions:
- enderdragonphase{phases=FLY_TO_PORTAL,LEAVE_PORTAL} true
```

## Aliases
- [x] edragonPhase
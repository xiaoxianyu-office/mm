## Description
Tests if the entity type of the target is the specified one.  
A list of valid entity types can be found on the [Spigot Javadocs](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | types, t  | A list of entity types to match                                      |<!--type:EntityType--><!--list--> |


## Examples
```yaml
Conditions:
- entitytype{t=ZOMBIE} true
```

```yaml
TargetConditions:
- entitytype{t=WITCH} true
```

```yaml
TriggerConditions:
- entitytype{t=PLAYER} true
```

## Aliases
- [x] mobtype
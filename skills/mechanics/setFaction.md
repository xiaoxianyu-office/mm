## Description
Sets or changes the target mob's faction.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| faction   | f         | The name of the faction to apply to the mob                          |         |


## Examples
Sets the faction of the mob to "Hostile" when the mob spawns.
```yaml
  Skills:
  - setFaction{faction=Hostile} @self ~onSpawn
```
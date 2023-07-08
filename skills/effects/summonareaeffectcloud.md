## Description 
Creates a cloud of particles around the target

A list of particle types can be found **[here](/skills/effects/particles/types)**. 

[All of the spigot particle effects listed in the javadocs should be acceptable as well.](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)

## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d         | The duration of the cloud                             | 200 |
| radius       | r      | The cloud's radius                                                                                       | 2 |
| durationreductiononuse  | drou         | The duration reduction for the cloud on use     | 0 |
| radiusreductiononuse       | rrou      | The radius reduction for the cloud on use                                                                                       | 0 |
| radiusreductionontick       | rrot      | The radius reduction for the cloud per tick                                                                                       | 0 |

## Examples
```yaml
  - summonareaeffectcloud{d=600;r=20;rrot=1} @self
```
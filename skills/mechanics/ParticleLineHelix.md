## Description 
Creates a particle line helix effect at the targeted entity or location.

A list of particle types can be found **[here](/skills/effects/particles/types)**. 

[All of the spigot particle effects listed in the javadocs should be acceptable as well.](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html)

## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| StartYOffset  | syo         | The starting vertical offset                             | 0 |
| TargetYOffset  | tyo         | The target vertical offset     | 0 |
| DistanceBetween       | db      | The distance between particles                                                                                       | 1 |
| FromOrigin    | fo  | Cast from origin?                                     | false |
| HelixLength   | hl    | The length of the helix effect                                 | 2 |
| HelixRadius   | hr        | The radius of the helix                               | 1 |
| HelixRotation   | rot | The rotation of the helix                           | 0 |
| maxdistance   | md        | The maximum distance for the helix              | 256 |


## Examples
```yaml
- effect:particlelinehelix{Fo=true;db=0.4;hl=4;syo=1.8;p=scrape;hr=0.5;md=40} @targetlocation
```
![Image](https://i.imgur.com/b812UFl.png)
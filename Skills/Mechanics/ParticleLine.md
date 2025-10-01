## Description
Creates a line of particles from the caster to the targeted entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distanceBetween | db  | The distance between each point in the line                          | 0.25    |
| startYOffset    | syo, ystartoffset, ys| Offset Y location of the starting point of the line | 0       |
| targetYOffset   | tyo, ytargetoffset, yt | Offset Y location of the target point of the line | 0       |
| fromOrigin      | fo  | Whether to draw the line from the [@origin] instead                  | false   |
| zigzag          | zz  | Whether to draw the line to the target as a zigzag                   | false   |
| zigzags         | zzs | Amount of zigzags when using the zigzag option                       | 10      |
| zigzagOffset    | zzo | Offset of each zigzag                                                | 0.2     |
| maxdistance     | md  | The maximum distance the line can reach                             | 256      |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic
>> The particles are generated “per point” in this mechanic, so keeping `amount` low is recommended.


## Examples
```yaml
FlameParticleLine:
  Skills:
  - particleline{particle=flame;amount=1;fromOrigin=true} @target
```


## Aliases
- [x] effect:particleline
- [x] e:pl
- [x] pl


<!-- LINKS -->
[@origin]: /skills/targeters/origin



<!--TAGS-->
<!--tag:Effect:Particle-->

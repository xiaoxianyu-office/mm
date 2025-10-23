## Description 
Creates a particle line helix effect at the targeted entity or location.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distanceBetween | db  | The distance between each point                                      | 1       |
| startYOffset    | syo, ystartoffset, ys| Offset Y location of the starting point             | 0       |
| targetYOffset   | tyo, ytargetoffset, yt | Offset Y location of the target point             | 0       |
| fromOrigin      | fo  | Whether to draw the line from the [@origin] instead                  | false   |
| helixlength     | hl  | The length of the helix effect                                       | 2       |
| helixradius     | hr  | The radius of the helix effect                                       | 1       |
| helixrotation   | rot | The rotation of the helix effect                                     | 0       |
| maxdistance     | md  | The maximum distance the line can reach                              | 256     |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic
>> The particles are generated “per point” in this mechanic, so keeping `amount` low is recommended.


## Examples
```yaml
  Skills:
  - particlelinehelix{Fo=true;db=0.4;hl=4;syo=1.8;p=scrape;hr=0.5;md=40} @targetlocation
```
<details><summary>Resulting effect</summary>
![Image](https://i.imgur.com/b812UFl.png)
</details>


## Aliases
- [x] effect:particlelinehelix
- [x] particlehelixline


<!-- LINKS -->
[@origin]: /skills/targeters/origin



<!--TAGS-->
<!--tag:Effect:Particle-->

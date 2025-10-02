## Description 
Creates a particleline ring.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distanceBetween | db  | The distance between each point                                      | 1       |
| startYOffset    | syo, ystartoffset, ys| Offset Y location of the starting point             | 0       |
| targetYOffset   | tyo, ytargetoffset, yt | Offset Y location of the target point             | 0       |
| fromOrigin      | fo  | Whether to draw the line from the [@origin] instead                  | false   |
| ringpoints | rp       | The number of points in the line ring                                | 16      |
| ringradius | rr       | The radius of the line ring                                          | 0.5     |
| maxdistance     | md  | The maximum distance the line can reach                              | 256     |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Examples
```yaml
  Skills:
  - particlelinering{p=flame;r=3;rr=1} @PIR{r=20;limit=1;sort=RANDOM}
```


## Aliases
- [x] effect:particlelinering
- [x] particleringline


<!-- LINKS -->
[@origin]: /skills/targeters/origin



<!--TAGS-->
<!--tag:Effect:Particle-->

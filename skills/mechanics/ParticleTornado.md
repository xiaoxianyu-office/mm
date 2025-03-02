## Description
Creates a tornado styled particle effect.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| maxradius | mr        | Max radius of the highest tornado “disk” shape                       | 3       |   
| yoffset   | yo        | The yoffset of the effect                                            | 0.8     | 
| height    | h         | # of disks desired * 2 + 1                                           | 4       |
| interval  | i         | How fast the particles vertically render. This can be experimented with “rotationspeed” as well                                                                        | 4       |
| duration  | d         | Duration of the effect in ticks                                      | 200     |
| rotationspeed | rs    | How fast the particles will horizontally render. This can be experimented with “interval” as well                                                                             | 0.04    |
| sliceheight | sh      | Any value below 1 will cause an incomplete tornado, while anything above 10 will cause different sized spheres to appear in a strange order. This has yet to be fully defined   | 64      |
| stoponcasterdeath | scd | Whether the effect should stop upon the death of its caster        | true    |
| stoponentitydeath | sed |Whether the effect should stop upon the death of the entity it is used on|true|
| cloudparticle | cp    | The particle type at the base of the tornado. Typically something like the “impact” as a tornado spins around, hence the largeexplode default value                    |largeexplode<!--type:Particle-->|
| cloudsize | cs        | The radius of the cloud's particle appearances                       | 5       |
| cloudamount | ca      | How many particles will appear at each randomly generated cloud location. | 1  |
| cloudhspread | chs    | The horizontal spreading of the cloud.                               | 1       |
| cloudvspread | cvs    | The vertical spreading of the cloud.                                 | 1.8     |
| cloudpspeed  | cps    | Speed of the playing of the cloud particles                          | 2       |
| cloudyoffset | cyo    | Y Offsetting of the entire tornado. (1 + your desired height)        | 1.8     |
> This mechanic inherits every attribute of the [Particle](/skills/mechanics/particle) mechanic


## Examples
```yaml
ExplodingTornado:
  Skills:
  - particletornado{p=flame;cp=largeexplode;mr=1;h=3;i=4;d=100;rs=1;sh=1;cs=0;ca=0;chs=0.1;cvs=0.1;cps=1;cyo=2} @self ~onTimer:100
```


## Aliases
- [x] effect:particletornado
- [x] e:pt


<!--TAGS-->
<!--tag:Effect:Particle-->

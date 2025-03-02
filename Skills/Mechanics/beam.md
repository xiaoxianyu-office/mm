## Description
Creates a beam of a material between the caster and the target


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onhitskill | onhit, oh | The skill to execute when the beam hits an entity. Currently not supported |<!--type:Metaskill-->|
| ontickskill | ontick, ot | The skill to execute each tick. The origin will be the starting location |<!--type:Metaskill-->|
| duration   | d        | Duration of the beam in ticks                                        | 20      |
| tickinterval | interval, i | Tick interval of the beam                                       | 1       |
| material   | m        | Material of the beam                              | END_ROD<!--type:Material-->|
| rotationspeed | rs    | Rotation speed of the beam in degrees per tick                       | 0       |
| hitradius | radius, r | Hit Radius of the beam                                               | 1.0     |
| startyoffset | syo    | The starting y offset of the beam from the caster's location         | 0       |
| endyoffset | eyo      | The end y offset of the beam from the target's location              | 0       |


## Examples
```yaml
  Skills:
  - beam{d=100;rs=2;syo=100} @selflocation
```


<!--TAGS-->
<!--tag:Meta-Mechanic-->
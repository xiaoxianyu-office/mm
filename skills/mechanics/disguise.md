## Description
Runs a disguise string on the casting mob. This skill requires Libs'
Disguises to be installed to enable Disguise functionality.

See [Add-On: Disguises](/Mobs/Disguises) for a list of available
disguises.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| disguise  | d, type   | The disguise to apply to the mob.                             | player Ashijin |
| audience  |           | The [audience] of the disguise                           |<!--type:Audience--> |


## Examples
> You can test cast both of these disguises with ``/mm test cast TestingDisguiseMechanic``

##

```yml
TestingDisguiseMechanic:
  Skills:
  - disguise{d="Sheep SetBurning SetSpinning"} @self
```
> This will disguise you as a sheep that is on fire and spinning.

##

```yml
TestingDisguiseMechanic:
  Skills:
  - disguise{d="Zombie setYModifier -1.5 setPitchLocked setInvisible setHelmet PLAYER_HEAD"} @self
```
> This example will turn you into a steve head that glides across the floor. No good way to describe it. It is pretty funny. I recommend you try it out!


<!-- LINKS -->
[audience]: /Skills/Audience


<!--TAGS-->
<!--tag:Disguise-->
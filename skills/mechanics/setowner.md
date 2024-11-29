## Description
Sets the "owner" attribute of the Mythic Mob to the given target. This is a special attribute used within MythicMobs, and different from the normal "vanilla" owner of a mob.  

Does nothing if the caster is not a Mythic Mob.  
If the casting mob is a `Wolf`,`Cat` or `Parrot` and the target is a Player, then the mechanic will _also_ set their Vanilla Owner as the targeted player.  

Works with the [@Owner Targeter](/Skills/Targeters/Owner), and the [Owner Condition](/skills/conditions/owner).  

While an Owner is set, a mob will never attack or target it, even if specified otherwise. A mob will still retain any aggro it had against the owner before it was set as such.


## Attributes
> *This mechanic has no attributes*


## Examples
```yaml
PetSheep:
  Mobtype: sheep
  Display: 'Pet'
  Health: 20
  Damage: 18
  Skills:
  - skill{s=SetOwner} @trigger ~onInteract
  - skill{s=HealOwner} @Owner ~onTimer:50
```

```yaml
SetOwner:
  Skills:
  - setowner
  - message{m=You are now the owner of this mob!}
```
> This skill would change the mob's owner to whoever right clicked it.
##
```yaml
HealOwner:
  Cooldown: 10
  TargetConditions:
  - health{h=<20} true
  Skills:
   - heal{a=10}
   - message{m=I healed you!}
```
> This skill would only heal the owner of the mob once every 10 seconds and only if they have less than 20 points of health left


<!--TAGS-->
<!--tag:Meta-->

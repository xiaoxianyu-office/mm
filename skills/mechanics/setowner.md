## Description
Sets the "owner" attribute of the Mythic Mob to the given target. This is a special attribute used within MythicMobs, and different from the normal "vanilla" owner of a mob.  
Does nothing if the caster is not a Mythic Mob, or the target is not a Player.  
Works with the [@Owner Targeter](/Skills/Targeters/Owner), and the [Owner Condition](/skills/conditions/owner).  

If the casting mob is a `Wolf`,`Cat` or `Parrot`, then the mechanic will _also_ set their Vanilla Owner as the targeted player.


## Attributes
>*This mechanic has no attributes*


## Examples
```yaml
PetSheep:
  Mobtype: sheep
  Display: 'Pet'
  Health: 20
  Damage: 18
  Skills:
  - skill{s=SetOwner} @trigger ~onInteract
  - skill{s=HealOwner} @PIR{R=10} ~onTimer:50
```

This skill would change the mob's owner to whoever right clicked it.
```yaml
SetOwner:
  Skills:
  - setowner @trigger
```
This skill would only heal the owner of the mob
```yaml
HealOwner:
  TargetConditions:
  - owner true
  Skills:
   - heal{a=10}
```
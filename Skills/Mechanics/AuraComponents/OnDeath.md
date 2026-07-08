## Description
Applies an aura component to the target that triggers a skill when they die


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onDeathSkill | od     | Skill to execute if the target dies                                  |<!--type:Metaskill-->|
| cancelEvent | cE, cancel | On Paper servers, cancels the death event and revives the mob when the skill runs successfully | false   |


## Examples
Force an onDeath aura through sudoskill on all entities around you. When you kill them they will all drop diamonds. 
```yaml
ForceApplyAura:
  Skills:
  - sudoskill{s=ApplyAura} @EIR{r=50}
ApplyAura:
  Skills:
  - aura{d=1200;i=1;auraname=rip;components=[
    - onDeath{od=DropDiamonds}
    ]} @self
DropDiamonds:
  Skills:
  - dropitem{i=DIAMOND 3-5} @self
```

On Paper servers, use `cancelEvent` to revive the mob instead of letting it
die. Here the mob has one charge, so it survives death once and plays an effect
before dying normally the next time.
```yaml
Undying:
  Skills:
  - aura{d=-1;charges=1;auraname=undying;components=[
    - onDeath{od=Revive;ce=true}
    ]} @self
Revive:
  Skills:
  - effect:particles{p=totem_of_undying;amount=50} @self
```

## Aliases
- [x] onDead


<!-- LINKS -->
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:Event-->

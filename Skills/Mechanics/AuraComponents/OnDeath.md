## Description
Applies an aura component to the target that triggers a skill when they die


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onDeathSkill | od     | Skill to execute if the target dies                                  |<!--type:Metaskill-->|


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

## Aliases
- [x] onDead


<!-- LINKS -->
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:Event-->

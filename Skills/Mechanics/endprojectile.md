## Description
Terminates the projectile this mechanic has been called from, activating its onEnd skill in the process.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| conditions| condition, cond, con | The conditions to check before terminating the projectile |<!--type:Conditions-->|

##Examples

**Mob file**
```yaml
Mob:
  Type: HUSK
  Skills:
  - skill{s=ExplodingProjectile} @target ~onTimer:20
  - aura{auraName=explode;d=2} @self ~onTimer:200
```

**Skill file**
```yaml
ExplodingProjectile:
  Skills:
  - projectile{onTick=ExplodingProjectile_Tick;onEnd=ExplodingProjectile_End;v=4;i=1;hp=false;sb=false;se=false;d=200}
ExplodingProjectile_Tick:
  Skills:
  - effect:particles{p=flame;amount=20;speed=0;hS=0.2;vS=0.2} @origin
  - sound{s=entity.blaze.burn;v=0.5} @origin
  - damage{a=2} @EntitiesNearOrigin{r=2}
  - endprojectile ?hasaura{auraName=explode}
ExplodingProjectile_End:
  Skills:
  - damage{a=20} @EntitiesNearOrigin{r=5}
  - throw{fromorigin=true} @EntitiesNearOrigin{r=5}
  - effect:explosion @origin
```


## Aliases
- [x] terminateProjectile
- [x] terminateproj
- [x] endproj
- [x] stopprojectile
- [x] stopproj


<!--TAGS-->
<!--tag:Meta-->

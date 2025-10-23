## Description
Applies an aura to the target that triggers a skill when they swing (left click)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onSwing   | onswingskill, osw | Skill to execute if the target swings / left clicks          |<!--type:Metaskill-->|

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
Simple:

Apply an onSwing aura to yourself and catch any entities in front and within 10 blocks of you on fire.
```yaml
ApplyAura:
  Skills:
  - onSwing{osw=CatchOnFire;auraname=Ignite;d=300;i=1} @self
CatchOnFire:
  Skills:
  - ignite{t=60} @EntitiesInCone{angle=90;range=10;rotation=0}
```

##

Intermediate:

Apple on onSwing aura to yourself that shoots out a projectile whenever you swing. It will play the skeleton shoot sound when the projectile spawns, have flame particles and a firecharge while it travels, and will deal between 2-4 MAGIC damage. 

```yaml
ApplyAura:
  Skills:
  - onSwing{osw=ShootProjectile;auraname=Fireballs;d=300;i=1} @self
ShootProjectile:
  Skills:
  - projectile{bulletType=ITEM;material=FIRE_CHARGE;bulletSpin=29;i=1;v=24;mr=100;d=100;hnp=true;oS=Fireball_oS;oT=Fireball_oT;oH=Fireball_oH} @forward{f=300;y=0}
Fireball_oS:
  Skills:
  - sound{s=entity.skeleton.shoot;v=1;p=1} @origin
Fireball_oT:
  Skills:
  - particles{particle=flame;a=4;hs=0.2;vs=0.2;y=0;s=0.1} @origin
Fireball_oH:
  Skills:
  - damage{a=2-4;cause=magic}
```


## Aliases
- [x] onleftclick


<!-- LINKS -->
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->

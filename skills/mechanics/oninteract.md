## Description
Applies an aura to a PLAYER that triggers a skill when they interact (right click) while holding an item, or are looking at a block (NOT AIR) that gets outlined (5 block range).

Applies an aura to an entity that triggers a skill when they are interacted with (gets right clicked) by a player


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onrightclickskill | oninteractskill, onrightclick, oninteract, or, oi | Skill to execute if the target player interacts with a block or the target entity is interacted by a player                   |<!--type:Metaskill-->|

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
Simple 1: (Player has aura)

Apply onInteract aura to yourself that gives you potion effects when you right click a block that is outlined (one within the 5 block range) OR you are holding an item while you right click.

```yaml
ApplyAura:
  Skills:
  - onInteract{or=PotionEffects;auraname=GodMode;d=300;i=1} @self
PotionEffects:
  Skills:
  - potion{t=DAMAGE_RESISTANCE;d=200;l=10;hasParticles=false} @self
  - potion{t=FIRE_RESISTANCE;d=200;l=10;hasParticles=false} @self
  - potion{t=REGENERATION;d=200;l=10;hasParticles=false} @self
  - potion{t=ABSORPTION;d=200;l=10;hasParticles=false} @self
```

##

Simple 2: (Player forces the Aura on nearby entities)

Use sudoskill to force nearby entities with 30 blocks to apply the onInteract aura on themselves. Then right click any of the entities to give the potion effects to all other entities in a range of 30 blocks. 

```yaml
ForceApplyAura:
  Skills:
  - sudoskill{s=ApplyAura} @EntitiesInRadius{r=30}
ApplyAura:
  Skills:
  - onInteract{or=PotionEffects;auraname=GodMode;d=300;i=1} @self
PotionEffects:
  Skills:
  - potion{t=DAMAGE_RESISTANCE;d=200;l=10;hasParticles=false} @EIR{r=30}
  - potion{t=FIRE_RESISTANCE;d=200;l=10;hasParticles=false} @EIR{r=30}
  - potion{t=REGENERATION;d=200;l=10;hasParticles=false} @EIR{r=30}
  - potion{t=ABSORPTION;d=200;l=10;hasParticles=false} @EIR{r=30}
```

##

Simple 3: (Player has aura and forces near by entites to execute a skill)

Apply onInteract aura to yourself that when you right click a block in your hand OR right click an outlined block (5 block range) it will send all mobs around you to the moon then after 5 seconds makes them smash back into the ground.

```yaml
ApplyAura:
  Skills:
  - onInteract{or=ToTheMoonStart;auraname=HerculesStrength;d=300;i=1} @self
ToTheMoonStart:
  Skills:
  - sudoskill{s=ToTheMoon} @EntitiesInRadius{r=10;targetPlayers=false}
ToTheMoon:
  Skills:
  - jump{v=10;repeat=4;repeatInterval=20} @self
  - delay 100
  - jump{v=-50} @self
```

##

Intermediate: (Player has aura)

Apply onInteract aura to yourself and when you right click an outlined block (5 block range) OR right click with an item in your hand cause a circular ring of tremors to grow outwards damaging and sending any hit entities flying backwards.

```yaml
ApplyAura:
  Skills:
  - onInteract{or=Tremors;auraname=Earthquakes;d=300;i=1} @self
Tremors:
  Skills:
  - blockwave{m=sand;d=20;r=2;n=0.85;v=1.5;vh=3;hsb=false} @ring{r=3;points=10}
  - blockwave{m=sand;d=20;r=2;n=0.825;v=1.5;vh=3;hsb=false;delay=20} @ring{r=5;points=15}
  - blockwave{m=sand;d=20;r=2;n=0.8;v=1.5;vh=3;hsb=false;delay=30} @ring{r=6;points=20}
  - blockwave{m=sand;d=20;r=2;n=0.775;v=1.5;vh=3;hsb=false;delay=40} @ring{r=7;points=25}
  - blockwave{m=sand;d=20;r=2;n=0.75;v=1.5;vh=3;hsb=false;delay=50} @ring{r=8;points=30}
  - blockwave{m=sand;d=20;r=2;n=0.725;v=1.5;vh=3;hsb=false;delay=60} @ring{r=9;points=35}
  - blockwave{m=sand;d=20;r=2;n=0.7;v=1.5;vh=3;hsb=false;delay=70} @ring{r=10;points=40}
  - blockmask{m=sand;d=20;r=3} @self
  - blockmask{m=sand;d=20;r=4;delay=10} @self
  - blockmask{m=sand;d=20;r=5;delay=20} @self
  - blockmask{m=sand;d=20;r=6;delay=30} @self
  - blockmask{m=sand;d=20;r=7;delay=40} @self
  - blockmask{m=sand;d=20;r=8;delay=50} @self
  - blockmask{m=sand;d=20;r=9;delay=60} @self
  - blockmask{m=sand;d=20;r=10;delay=70} @self
  - damage{a=3-5;cause=ENTITY_ATTACK} @EntitiesInRing{min=0.5;max=3.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=10} @EntitiesInRing{min=3.5;max=4.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=20} @EntitiesInRing{min=4.5;max=5.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=30} @EntitiesInRing{min=5.5;max=6.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=40} @EntitiesInRing{min=6.5;max=7.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=50} @EntitiesInRing{min=7.5;max=8.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=60} @EntitiesInRing{min=8.5;max=9.5}
  - damage{a=3-5;cause=ENTITY_ATTACK;delay=70} @EntitiesInRing{min=9.5;max=10.5}
  - aura{d=20;i=1;oT=Tremors_oT} @EntitiesInRing{min=0.5;max=3.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=10} @EntitiesInRing{min=3.5;max=4.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=20} @EntitiesInRing{min=4.5;max=5.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=30} @EntitiesInRing{min=5.5;max=6.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=40} @EntitiesInRing{min=6.5;max=7.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=50} @EntitiesInRing{min=7.5;max=8.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=60} @EntitiesInRing{min=8.5;max=9.5}
  - aura{d=20;i=1;oT=Tremors_oT;delay=70} @EntitiesInRing{min=9.5;max=10.5}
Tremors_oT:
  Skills:
  - throw{v=20;vy=3}
```


<!-- LINKS -->
[aura]: /skills/mechanics/aura



<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->

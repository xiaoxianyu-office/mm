## Description
Applies an aura component to a PLAYER that triggers a skill when they interact (right click) while holding an item, or are looking at a block (NOT AIR) that gets outlined (5 block range).

Applies an aura component to a non-player entity that triggers a skill when they are interacted with (gets right clicked) by a player


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onrightclickskill | oninteractskill, onrightclick, oninteract, or, oi | Skill to execute if the target player interacts with a block or the target entity is interacted by a player                   |<!--type:Metaskill-->|


## Examples
Simple 1: (Player has aura)

Apply onInteract aura to yourself that gives you potion effects when you right click a block that is outlined (one within the 5 block range) OR you are holding an item while you right click.

```yaml
ApplyAura:
  Skills:
  - aura{auraname=GodMode;d=300;i=1;components=[
    - onInteract{or=PotionEffects}
    ]} @self
PotionEffects:
  Skills:
  - potion{t=DAMAGE_RESISTANCE;d=200;l=10;hasParticles=false} @self
  - potion{t=FIRE_RESISTANCE;d=200;l=10;hasParticles=false} @self
  - potion{t=REGENERATION;d=200;l=10;hasParticles=false} @self
  - potion{t=ABSORPTION;d=200;l=10;hasParticles=false} @self
```

---

Simple 2: (Player forces the Aura on nearby entities)

Use sudoskill to force nearby entities with 30 blocks to apply the onInteract aura on themselves. Then right click any of the entities to give the potion effects to all other entities in a range of 30 blocks. 

```yaml
ForceApplyAura:
  Skills:
  - sudoskill{s=ApplyAura} @EntitiesInRadius{r=30}
ApplyAura:
  Skills:
  - aura{auraname=GodMode;d=300;i=1;components=[
    - onInteract{or=PotionEffects}
    ]} @self
PotionEffects:
  Skills:
  - potion{t=DAMAGE_RESISTANCE;d=200;l=10;hasParticles=false} @EIR{r=30}
  - potion{t=FIRE_RESISTANCE;d=200;l=10;hasParticles=false} @EIR{r=30}
  - potion{t=REGENERATION;d=200;l=10;hasParticles=false} @EIR{r=30}
  - potion{t=ABSORPTION;d=200;l=10;hasParticles=false} @EIR{r=30}
```

---

Simple 3: (Player has aura and forces nearby entities to execute a skill)

Apply onInteract aura to yourself that when you right click a block in your hand OR right click an outlined block (5 block range) it will send all mobs around you to the moon then after 5 seconds makes them smash back into the ground.

```yaml
ApplyAura:
  Skills:
  - aura{auraname=HerculesStrength;d=300;i=1;components=[
    - onInteract{or=ToTheMoonStart}
    ]} @self
ToTheMoonStart:
  Skills:
  - sudoskill{s=ToTheMoon} @EntitiesInRadius{r=10;targetPlayers=false}
ToTheMoon:
  Skills:
  - jump{v=10;repeat=4;repeatInterval=20} @self
  - delay 100
  - jump{v=-50} @self
```


## Aliases
- [x] onrightclick


<!-- LINKS -->
[aura]: /skills/mechanics/aura

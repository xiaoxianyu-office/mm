These skills are usually triggered by a player when using an item, and utilizing [Mythic Crucible](https://git.lumine.io/mythiccraft/mythiccrucible).
### Eat Food Skill
----------
* A food consumption example skill that, when used, replenishes saturation and gives a short burst of the saturation potion effect while playing three sounds and particle on a slight delay.

```yaml
eatmeal:
  Skills:
  - feed{amount=10;overfeed=true} @self
  - effect:particles{p=happy_villager;amount=5;speed=.5;y=1} @self
  - effect:sound{s=minecraft:entity.experience_orb.pickup;v=0.8;p=0.6} @self
  - Delay 2
  - effect:sound{s=minecraft:entity.experience_orb.pickup;v=0.8;p=0.7} @self
  - Delay 2
  - effect:sound{s=minecraft:entity.experience_orb.pickup;v=0.8;p=0.8} @self
  - potion{t=SATURATION;d=100;l=2;force=true} @self
```

---

### Drink Flight Potion Skill
----------
* A potion consumption spell that, when used, grants the consumer with the ability to fly for 1 minute, with a bossbar that counts down the duration remaining, and particles to show the effect is active.

```yaml
basicflypot:
  Conditions:
  Skills:
  - effect:sound{s=entity.generic.drink;v=1;p=1} @self
  - effect:particles{p=fireworks_spark;amount=20;speed=.5;y=1} @self
  - effect:sound{s=block.end_portal_frame.fill;v=0.3;p=2} @self
  - effect:sound{s=item.bottle.fill_dragonbreath;v=0.3;p=0.8} @self
  - effect:sound{s=minecraft:block.beacon.power_select;v=1;p=1.4} @self
  - effect:particles{p=ELECTRIC_SPARK;amount=10;speed=.8;y=1} @self
  - fly{duration=1200;ot=flightaura;i=20;bt=true;auraName=Flight Remaining:} @self
flightaura:
  Skills:
  - effect:particles{p=fireworks_spark;amount=5;speed=.1;y=1} @self
```
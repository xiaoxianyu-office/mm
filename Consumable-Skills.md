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
* _todo_
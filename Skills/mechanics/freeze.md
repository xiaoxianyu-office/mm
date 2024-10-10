## Description
Sets the ticks frozen in powdered snow. Freeze ticks are capped at 140 ticks for players. (requires 1.17)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| ticks     | t, duration, d | Ticks frozen in powdered snow                                   | 60      |


## Examples
Freezes the entity that the mob using this skill is attacking for 100
ticks (5 seconds).
```yaml
  Skills:
  - freeze{ticks=100} @trigger ~onAttack
```
It's possible that the method above may not work due to how the game handles the freezing status. In case that happens, it's still possible to do something like the following
```yaml
#Inline version for premium users
Freeze_CauseFreezeEffect_Inline:
  Skills:
  - aura{d=100;i=1;onTick=[  - freeze{ticks=280} - damage{a=1;cd=2;damagecause=FREEZE} ]} @self

#Normal version
Freeze_CauseFreezeEffect_Normal:
  Skills:
  - aura{d=100;i=1;onTick=Freeze_CauseFreezeEffect_Normal_onTick} @self
Freeze_CauseFreezeEffect_Normal_onTick:
  Skills:
  - freeze{ticks=280}
  - damage{a=1;cd=2;damagecause=FREEZE}
```
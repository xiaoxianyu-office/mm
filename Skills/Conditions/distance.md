## Description
Whether the distance between the caster and target is within the given range.  
Can be a single number, a ranged value (20to40), or >10 <5, etc.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  |   d       | The distance to match                                                |         |


## Examples
```yaml
  TargetConditions:
  - distance{d=<2}
```

---

This example will spawn an armor stand with debug rings to show distance.  Depending on the player's distance from the armor stand, the mob will send a different message

```yaml
distance_mob:
  Type: ARMOR_STAND
  Skills:
  - particlering{p=redstone;points=20;r=3;a=1} @self ~onTimer:20
  - particlering{p=redstone;points=20;r=7;color=#00ff48;a=1} @self ~onTimer:20
  - particlering{p=redstone;points=20;r=10;color=#0059ff;a=1} @self ~onTimer:20
  - skill{s=distance_check} @PIR{r=10;limit=1;sort=NEAREST} ~onTimer:20
```

```yaml
distance_check:
  TargetConditions:
  - distance{d=0to3} castinstead distance_check_close
  - distance{d=3to7} castinstead distance_check_mid
  - distance{d=>7} castinstead distance_check_far
  Skills:
  - message{m="This message is never sent"}
distance_check_close:
  Skills:
  - message{m="<red><target.name> is close to the caster!"}
distance_check_mid:
  Skills:
  - message{m="<green><target.name> is medium distance from the caster!"}
distance_check_far:
  Skills:
  - message{m="<blue><target.name> is far from the caster!"}
```

> *This example was kindly provided by slipperysmurf*

## Description
Checks how many children the caster has.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount of children to check for. Can accept ranged values.       | 1       |



## Examples
```yaml
  Conditions:
  - children{a=1} true
```
```yaml
  Conditions:
  - children{a=>2} true
```

---

This example showcases a parent mob that will summon children until it reaches 3 total, and then will stop until 1 is killed or de-spawned

```yaml
children_overflow_mob:
  Type: ARMOR_STAND
  Skills:
  - skill{s=children_summon_more} @self ~onTimer:20
children_mob:
  Type: PIG
```

```yaml
children_summon_more:
  Conditions:
  - children{a=<3} orelsecast children_too_many
  Skills:
  - summon{m=children_mob;amount=1}
  - delay 0
  - message{m="<green>Child summoned, there are now <caster.children.size> children!"} @PIR{r=10}

children_too_many:
  Skills:
  - message{m="<red>No children summoned, already 3 or more!"} @PIR{r=10}
```

> *This example was kindly provided by slipperysmurf*

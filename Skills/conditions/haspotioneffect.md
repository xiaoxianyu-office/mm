## Description
Tests if the target entity has a potion effect


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The potion effect type                                               | ANY<!--type:PotionEffectType--> |
| level     | lvl, l    | An optional level range to match                                     |         |
| duration  | d         | An optional duration range to match                                  |         |


## Examples
```yaml
  Conditions:
  - haspotioneffect{t=SLOW;l=0-2;d=0-9999} true
```

```yaml
  TargetConditions:
  - haspotioneffect{t=Speed;l=0-9} true
```


## Aliases
- [x] hasPotion
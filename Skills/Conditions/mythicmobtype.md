## Description
Checks the MythicMob type of the target mob


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | types, t  | A list of MythicMob types to match                                   |         |
| exactmatch | em       | Whether the types specified should exactly match the name of a MythicMob. If this attribute is set to `false`, this condition will also work if the evaluated entity's MythicMob name only *contains* any of the specified types | true |


## Examples
```yaml
  Conditions:
  - mythicmobtype{t=CoolZombie,IceZombie,SnowZombie} true
```

```yaml
  TargetConditions:
  - mythicmobtype{t=HotZombie,LavaZombie,FireZombie} true
```


## Aliases
- [x] mmType
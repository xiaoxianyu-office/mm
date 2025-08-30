## Description
Checks if value1 equals value2. Both values can use [variables](/Skills/Variables) and [placeholders](/Skills/Placeholders).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| value1    | val1, v1, string, s                     | The first value                        |         |
| value2    | val2, v2, value, val, v, equals, eq, e  | The second value                       |         |


## Examples
```yaml
  Conditions:
  - stringequals{val1="yes!";val2="yes!"} true
```
```yaml
  Conditions:
  - stringequals{val1="%denizen_<player[<trigger.uuid>].item_in_hand.has_nbt[special_item]>%";val2="true"} true
```
Uses Denizen, PlaceholderAPI, and MythicMobs to check whether the item the player is holding has a Denizen NBT key of “special_item.” <trigger.uuid> is a MythicMobs placeholder that gets parsed before PlaceholderAPI parses the Denizen tag.
```yaml
  Conditions:
  - stringequals{val1="%denizen_<player[<trigger.uuid>].item_in_hand.raw_nbt.get[mythic_type].after[string:]>%";val2="SomeMythicItem"} true
```


## Aliases
- [x] stringEq
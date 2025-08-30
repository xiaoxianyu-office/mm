## Description
Checks a scoreboard value of the target entity.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| objective | obj, o    | The objective                                                        |         |
| entry     | ent, e    | The entry                                                            |         |
| value     | val, v    | The value to match                                                   |         |


## Examples
```yaml
  Conditions:
  - score{o=PlayerKills;e=Akim91;v=10} true
```
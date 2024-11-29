## Description 
Copies the appearance of the target player. Does nothing if the target is not a player. This skill requires Libs' Disguises to be installed to enable disguise-functionality.


## Attributes 
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| hasnameplate | nameplate | Whether the disguise should have a nameplate                      | true    |
| usePlayerName | upn |  Uses the player name as the nameplate                                 |         |


## Examples
```yaml
TotallyNotDitto:
  Type: SKELETON
  Skills:
  - doppleganger @NearestPlayer ~onSpawn
```


## Aliases
- [x] copyplayer


<!--TAGS-->
<!--tag:Disguise-->
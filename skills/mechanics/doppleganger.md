## Description 
Copies the appearance of the target player. Does nothing if the target
is not a player. This skill requires Libs' Disguises and ProtocolLib to be
installed to enable disguise-functionality.


## Attributes 
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| usePlayerName |       |  Uses the player name as the new name                                |         |


## Examples
```yaml
TotallyNotDitto:
  Type: SKELETON
  Skills:
  - doppleganger @NearestPlayer ~onSpawn
```
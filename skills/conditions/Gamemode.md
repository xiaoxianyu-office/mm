## Description
Matches the target player's gamemode


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| mode      | m         | The gamemode to match                                                | SURVIVAL<!--type:Gamemode--> |

### Mode Attribute
Possible gamemodes are 
- `SURVIVAL`
- `CREATIVE`
- `ADVENTURE`
- `SPECTATOR`


## Examples
```yaml
ExampleSkill:
  Conditions:
  - gamemode{m=ADVENTURE} true
```


## Aliases
- [x] gm
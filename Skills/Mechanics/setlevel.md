## Description
Causes the casting mob to change its level.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| action    | a         | The type of the operation to perform                                 | SET<!--type:SET,ADD,SUBTRACT,MULTIPLY,DIVIDE-->|
| level     | l         | Amount used in the operation                                         | 1       |

  
## Action Attribute
Available actions are
- `SET`
- `ADD`
- `SUBTRACT`
- `MULTIPLY`
- `DIVIDE`


## Examples
This will set the mob level to 3 when it spawns
```yaml
    - setlevel{a=set;l=3} @self ~onSpawn
```
##
This will increase the mob level by 1 each time it kills a player
```yaml
    - setlevel{a=add;l=1} ~onKillPlayer
```
##
This will set the level of the mob to a random value between 1 and 5 when it spawns, plus the score of the `__GLOBAL__` fake player from the "testlevel" scoreboard.
```yaml
    - setlevel{a=set;l="<random.1to5> + <global.score.testlevel>"} @self ~onSpawn
```
> The usage of [Placeholders](/Skills/Placeholders) and [Math Operations](/Skills/Math) inside of a non-string attribute is [**Premium Only**](Premium-Features)

## Aliases
- [x] modifylevel
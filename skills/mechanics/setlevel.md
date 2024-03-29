## Description
Causes the casting mob to change its level.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| action    | a         | The type of the operation to perform                                 | SET     |
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

This will increase the mob level by 1 each time it kills a player
```yaml
    - setlevel{a=add;l=1} ~onKillPlayer
```


## Aliases
- [x] modifylevel
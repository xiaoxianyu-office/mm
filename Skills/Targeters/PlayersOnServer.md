## Description
Targets all players in the server


## Attributes
>*This targeter has no attributes*


## Examples
```yaml
PlayerCount_ServerWide:
  Skills:
  - setvariable{var=skill.count;val=<skill.targets>} @PlayersOnServer{targetself=true}
  - message{m="There are <skill.var.count> entities loaded in the current world"} @self
```


## Aliases
- [x] server
- [x] everyone
## Description
Targets all players in the caster's world


## Attributes
>*This targeter has no attributes*


## Examples
```yaml
PlayerCount:
  Skills:
  - setvariable{var=skill.count;val=<skill.targets>} @PlayersInWorld{targetself=true}
  - message{m="There are <skill.var.count> entities loaded in the current world"} @self
```


## Aliases
- [x] World
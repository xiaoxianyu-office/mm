## Description
Targets all living entities in the caster's world


## Attributes
>*This targeter has no attributes*


## Examples
```yaml
EntityCount:
  Skills:
  - setvariable{var=skill.count;val=<skill.targets>} @LivingInWorld
  - message{m="There are <skill.var.count> entities loaded in the current world"} @self
```


## Aliases
- [x] EIW
- [x] allinworld
- [x] livingentitiesinworld
- [x] entitiesinworld
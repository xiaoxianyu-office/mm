## Description
Sets a value of type string. The value will depend on the location passed to the "value" parameter, and will include informations regarding coordinates and world of the target location



## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| value     | val, v, a, amount | The target location                                          | @self   |
> This mechanic inherits every *inheritable* attribute of the [SetVariable](skills/mechanics/setvariable) mechanic


## Examples
```yaml
TestSkill:
 Skills:
 - setvarloc{var=caster.1;v=@self} @self
 - m{m=<caster.var.1>} @self
```


## Aliases
- [x] variableSetLocation
- [x] setVarLoc


<!--TAGS-->
<!--tag:Variable-->

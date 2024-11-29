## Description
Unsets a [variable](/skills/variables).


## Attributes
> This mechanic inherits every *inheritable* attribute of the [SetVariable](skills/mechanics/setvariable) mechanic


## Examples
This will unset the testing caster scope variable from the caster.

```yaml
RemoveVariable:
  Skills:
  - variableUnset{var=caster.testing} @self
```

This will unset the testing caster scope variable from the caster as well.
```yaml
RemoveVariable:
  Skills:
  - variableUnset{var=testing;scope=caster} @self
```


## Aliases
- [x] unsetvariable
- [x] unsetvar
- [x] varunset


<!--TAGS-->
<!--tag:Variable-->

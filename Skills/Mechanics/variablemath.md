## Description
Sets a variable to the result of a math equation, where 'x' is the
[variable](/skills/variables)'s current value.  

Basically a setvariable mechanic with some extra spices


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| equation  | eq, e     | The operation to be done, must be inside quotes                      | x       |
> This mechanic inherits every *inheritable* attribute of the [SetVariable](skills/mechanics/setvariable) mechanic

  
## Examples
Storing a placeholder in a variable
```yaml
    MMOVar:
      Skills:
      - variableMath{var=target.exp;equation="%mmocore_level%"}
```
Doing math
```yaml
    Math1:
      Skills:
      - variableMath{var=caster.damage;equation="<caster.hp>*5"}
    Math2:
      Skills:
      - variableMath{var=caster.speed;equation="(<caster.var.age>/5)+1"}
```

## Aliases
- [x] mathvariable
- [x] varmath
- [x] mathvar


<!--TAGS-->
<!--tag:Variable-->

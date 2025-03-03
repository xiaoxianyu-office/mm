## Description
Checks if the given [variable](/Skills/Variables) is set.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| variable  | name, n, var, key, k | The name of the variable. Can optionally be prefixed with scope|    |
| scope     | s         | The [scope](/Skills/Variables#variable-scopes) of the variable, e.g. where the variable is located                                                                            |<!--type:VariableScope-->|


## Examples
```yaml
  Conditions:
  - variableisset{var=target.dazed} true
```


## Aliases
- [x] varisset
- [x] varset
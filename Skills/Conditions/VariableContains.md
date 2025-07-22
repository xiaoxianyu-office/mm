## Descriptions
Checks if the given variable contains a certain value.
- For String variables, is it checked if the variable contains a substring. Based on the compareType used, it can also be checked if the variable "starts with" or "ends with" the given value.
- For List or Set variables
  - If the value is a simple string, it is checked if the List or Set contains the value
  - If the entry is another List or Set, it is checked if the variable contains all or any of the elements of the value, based on the compareType.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| variable  | name, n, var, key, k | The name of the variable. Can optionally be prefixed with scope|    |
| scope| s| The [scope](/Skills/Variables#variable-scopes) of the variable, e.g. where the variable is located                                                                                        |<!--type:VariableScope-->|
| compareType | compare, comp | The comparison type to use. Can be `ALL`, `ANY`, `STARTS_WITH` or `ENDS_WITH`. | ALL |
| value     | val, v    | The value of the comparison                                          |         |

### CompareType attribute
If the variable is a String, you can use either the `STARTS_WITH` or `ENDS_WITH` to check if the variable starts with or ends with the given value

If the variable is a List or Set and the value is also a List or Set, you can use `ALL` to check if all elements of the value are present in the variable, or `ANY` to check if at least one element is present


## Examples
```yaml
  Conditions:
  - variablecontains{var=skill.examplelist;val=hello}

  - variablecontains{var=skill.examplelist;val=hello,world;compareType=ANY}

  - variablecontains{var=skill.examplestring;val=pizza}

  - variablecontains{var=skill.examplestring;val=dungeon_;compareType=STARTS_WITH}
```


## Aliases
- [x] variableContain
- [x] varContains
- [x] varContain
- [x] varCont
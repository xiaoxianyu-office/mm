## Description
Moves an already created variable across names and/or registries. By default, no new variable is created, so this can be used to make two different registries reference the exact same variable, allowing the modifications on one to reflect on the other


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| from      |           | The variable to move, in the `scope.name` format                     |         |
| to        |           | Where the variable should end up, in the `scope.name` format         |         |
| removeOld |           | Whether the moved variable should be removed from the old variable registry | false |
| createNew |       | Whether a new variable should be created at the target variable registry | false   |
| inheritExpirationTime |  | If `createNew` is true, whether the new variable should inherit the expiration time from the old one | true |


## Examples
```yaml
  Skills:
  - setVar{name=caster.item;type=ITEM;value=slot:HAND} @self
  - movevariable{from=caster.item;to=skill.item} @self
  - equip{item=itemvariable{variable=skill.item} head} @self
```


## Aliases
- [x] moveVariable
- [x] moveVar
- [x] varMove
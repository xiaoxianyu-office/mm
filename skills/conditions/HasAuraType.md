## Description
Checks if the target entity has the given aura type


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | group, name, g, t, n | The aura type to check for                                |         |


## Examples
This example would apply an aura of a `Example` Type. The second example will then check for its presence
```yaml
  Skills:
  - aura{auraName=NotMeThisTime;auratype=Example;d=100} @self
```
```yaml
  Conditions:
  - hasAuraType{type=Example} true
```

## Aliases
- [x] hasbufftype
- [x] hasdebufftype
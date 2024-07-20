## Description
Checks if the target entity has the given aura


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| aura      | auraname, b, buff, buffname, debuff, debuffname, n, name | The name of the aura to check for   


## Examples
```yaml
  Conditions:
  - hasaura{aura=firedebuff} true
```


## Aliases
- [x] hasbuff
- [x] hasdebuff
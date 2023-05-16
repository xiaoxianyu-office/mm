## Description
Checks if the target entity has the given aura


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| auraName  | name, n, aura, buffname, buff, debuffname, debuff, b| The name of the aura to check for ||


## Examples
```yaml
  Conditions:
  - hasaura{n=firedebuff} true
```


## Aliases
- [x] hasbuff
- [x] hasdebuff
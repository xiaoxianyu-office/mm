## Description
Whether the distance from the world's spawn point to the target is within the given range


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  |   d       | The distance to match                                                |         |


## Examples
```yaml
  Conditions:
  - distancefromspawn{d=<100} true
```
```yaml
  Conditions:
  - distancefromspawn{d=>50} true
```
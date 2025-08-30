## Description
Checks is the server is running a specific minecraft NMS version


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| version   | sv, v     | The version to check for                                        | v1_19_R1_2 |


## Examples
```yaml
  Conditions:
  - nmsversion{v="v1_19_R1"}
```


## Aliases
- [x] servernms
- [x] nmsversion
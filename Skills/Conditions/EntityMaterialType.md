## Description
Tests the material of the targeted entity item


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | mat, m, type, types, t | A list of materials to match                            |<!--type:Material--><!--list--> |


## Examples
```yaml
  TargetConditions:
  - entityMaterialType{mat=STONE,DIRT} true
```
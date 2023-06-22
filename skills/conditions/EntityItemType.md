## Description
Tests the type of the targeted entity item


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | mat, m, type, types, t | A list of items to match                                |         |


## Examples
```yaml
  TargetConditions:
  - entityItemType{m=MyMythicItem,MyFantasticStick} true
```
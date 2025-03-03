## Description
Tests if the item entity is similar to an itemstack


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | i, material, m, mm, mythicitem | The item to check against                       | DIRT<!--type:Material-->|


## Examples
```yaml
  TargetConditions:
  - entityitemissimilar{i=MyCustomItem} true
```
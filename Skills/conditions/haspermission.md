## Description
This condition checks if the target player has a permission. 


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| permission| p         | The permission to check for.                                         |         |


## Examples

```yaml
  Conditions:
  - haspermission{p=permission.node.here} true
```
```yaml
  TargetConditions:
  - haspermission{p=permission.node.here} true
```
```yaml
  TriggerConditions:
  - haspermission{p=permission.node.here} true
```


## Aliases
- [x] permission
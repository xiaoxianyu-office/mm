## Description
Checks against the entity's size.  
Valid entities: `Slime`, `Magmacube`, `Phantom`


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| size      | s         | The size to check for                                                |         |


## Examples
```yaml
  TargetConditions:
  - size{s=>1} true
```


## Aliases
- [x] mobSize
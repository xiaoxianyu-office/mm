## Description
Tests if the target player or an item container has exactly the given number of the given material.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | i, material, m | The item to check for                                           | DIRT    |
| amount    | a         | The amount to check for                                              | >0      |


## Examples

```yaml
  Conditions:
  - hasitem{i=stick;amount=>1} true
```
```yaml
  Conditions:
  - hasitem{i=my_custom_item;amount=<10} true
```
```yaml
  Conditions:
  - hasitem{i=mmoitems.SWORD.CUTLASS;amount=1to10} true
```
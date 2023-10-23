## Description
Gives the target player an amount of oxygen.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    |           | the amount of oxygen to give the player                              |         |


## Examples
```yaml
  Skills:
  - oxygen{amount=10} @trigger ~onInteract
```
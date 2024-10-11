## Description
Gives the target player an amount of oxygen.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | the amount of oxygen to give the player                              | 1       |


## Examples
```yaml
  Skills:
  - oxygen{amount=10} @trigger ~onInteract
```
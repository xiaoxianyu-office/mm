## Description
Removes the given amount from the target player's held item. 


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount to remove                                                 | 1       |


## Examples
```yaml
ExampleSkill:
  Skills:
  - consumeHeldItem{amount=1} @trigger
```


## Aliases
- [x] consumeHeldItem
- [x] takeHeldItem
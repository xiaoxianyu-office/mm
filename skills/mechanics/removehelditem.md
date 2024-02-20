## Description
Removes the given amount from the casting player's held item. 

> **This is a no-target mechanic, and the affected entity will always be the caster**

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount to remove                                                 | 1       |


## Examples
```yaml
ExampleSkill:
  Skills:
  - removeHeldItem{amount=1} @trigger
```


## Aliases
- [x] consumeHeldItem
- [x] takeHeldItem
## Description
Checks if the target is holding a given material


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m, type, t| A material or MythicItem internal id to check for                    |         |


## Examples
```yaml
# Make sure you use all caps for materials, otherwise the console will say it is not a valid material!
  Conditions:
  - holding{m=DIAMOND_SWORD} true
```
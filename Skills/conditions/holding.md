## Description
Checks if the target is holding a given material


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m, type, t| A material, MythicItem or MMOItems internal id to check for                    |         |


## Examples
```yaml
# Make sure you use all caps for materials, otherwise the console will say it is not a valid material!
Conditions:
- holding{m=DIAMOND_SWORD} true
```
This is an example of using an item from MMOItems. mmoitems.category.item
```yaml
Conditions:
- holding{m=mmoitems.TOOL.PICKAXE_5} true
```
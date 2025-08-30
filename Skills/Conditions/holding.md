## Description
Checks if the target is holding a given material.  
Uses the [Item Matcher](/Items/Item-Matcher)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m, type, t, item, i, mat, types | A material, MythicItem or MMOItems internal id to check for |<!--type:Item-->|
| strict    | exact, e  | Whether the matcher should more strictly match the target item       | false   |
| vanillaonly | vanilla | Whether the matched item can only be a vanilla one                   | false   |


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


<!--TAGS-->
<!--tag:ItemMatcher-->
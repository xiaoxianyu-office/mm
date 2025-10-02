## Description
Removes the specified amount of an item from the target player's inventory.  
Uses the [Item Matcher](/Items/Item-Matcher)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | material, m, i, mat, t, type, types | The item, or material, to remove  | DIRT<!--type:Item-->|
| amount    | a              | The amount to remove                                            | 1       |
| exact     | e, strict | Whether the name of the item should match exactly to the specified one | true  |
| vanillaonly | vanilla | Whether the matched item can only be a vanilla one                   | false   |
| variable  | var       | The Item variable whose value is to be taken from the inventory. When set, `item` is ignored |


## Examples
Would remove a stack of dirt from the nearest player's inventory
```yaml
  Skills:
  - takeitem{i=DIRT;a=64} @NearestPlayer{r=10}
```

## Aliases 
- [x] take 
- [x] itemtake
- [x] takeitems


<!--TAGS-->
<!--tag:Item-->
<!--tag:Inventory-->
<!--tag:ItemMatcher-->
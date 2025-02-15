## Description
Steals an item from the target and puts it in the mob's hand


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| amount    | a         | The amount to steal                                                  | 1       |
| dropchance | dc | Sets the chance for the stolen item to be dropped upon death               | 0.0     |
| strict    | exact, e  | Whether the matcher should more strictly match the target item       | false   |
| types     | type, t, material, mat, m, item, i | The items to match. Can be a list           | DIRT    |
| onSteal   | then      | The Metaskill to execute once an item is successfully stolen         |         |

## Examples
```yaml
  Skills:
  - stealitem @trigger ~onDamaged 0.1 =100%
```


## Aliases
- [x] steal
- [x] stealitems
- [x] itemsteal


<!--TAGS-->
<!--tag:Item-->
<!--tag:Inventory-->
<!--tag:ItemMatcher-->
<!--tag:Meta-Mechanic-->
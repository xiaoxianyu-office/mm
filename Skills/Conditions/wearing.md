## Description
This condition checks if the target entity is wearing the selected item.  
Uses the [Item Matcher](/Items/Item-Matcher)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| armorslot | slot, s   | The [item slot](/Skills/EquipSlot) to check.       | HEAD<!--type:EquipSlot--> |
| material  | mat, m, item, i, t, type, types | A material or MythicItem name to check for. Also supports MMOItems in the format mmoitems.TYPE.ID                                               | DIRT <!--type:Item-->   |
| strict    | exact, e  | Whether the matcher should more strictly match the target item       | false   |
| vanillaonly | vanilla | Whether the matched item can only be a vanilla one                   | false   |

## Examples
```yaml
Conditions:
  - wearing{slot=HAND;m=IRON_SWORD} true
  - wearing{slot=CHEST;m=mmoitems.TYPE.ID} true
```


## Aliases
- [x] iswearing 
- [x] wielding 
- [x] iswielding


<!--TAGS-->
<!--tag:ItemMatcher-->
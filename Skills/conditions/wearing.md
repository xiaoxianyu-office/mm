## Description
This condition checks if the target entity is wearing the selected item.  


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| armorslot | slot, s   | The item slot to check.                                              | HEAD    |
| material  | mat, m, mythicmobsitem, mmitem, mmi, item | A material or MythicItem name to check for. Also supports MMOItems in the format mmoitems.TYPE.ID                                               | DIRT    |

**Valid Slots:**

| HEAD | CHEST | LEGS | FEET | HAND | OFFHAND |       
| ---- | ----- | ---- | ---- | ---- | ------- |  


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
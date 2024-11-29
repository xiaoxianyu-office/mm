## Description
Equips the mob with an item. Uses the exact same syntax as the
[Equipment](/mobs/equipment) configuration.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | items, i, equipment, equip, e | The item config string to run on the mob.           |      |


## Examples
This example would equip the casting mob with a diamond sword.
```yaml
EquipDiamondSword:
  Skills:
  - equip{item=diamond_sword HAND}
```

This example would equip the Skeleton King's crown as a helmet.
```yaml
EquipCrown:
  Skills:
  - equip{item=KingsCrown HEAD}
```


<!--TAGS-->
<!--tag:Item-->
<!--tag:Inventory-->
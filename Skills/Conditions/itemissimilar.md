## Description
Checks if the target player's inventory slot holds an item that is similar to the specified one.  
To be more specific, their ItemStacks will be compared and the condition will return true if they match.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | i, material, m, mm, mythicitem | The item to check for                           | DIRT<!--type:Item-->|
| slot      | s         | The inventory slot to check for. Accepts 0 to 35, or equipment slots | HAND<!--type:EquipSlot-->|


## Examples
Tests the item in slot 0, or the first slot, of the targeted player's inventory.
```yml
  Conditions:
  - itemissimilar{i=MyCustomItem;slot=0} true
```


## Aliases
- [x] issimilar
- [x] similarto
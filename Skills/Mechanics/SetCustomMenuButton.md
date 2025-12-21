## Description
Sets a specific slot of the opened [custom menu] to the specified button.  
Will work as long as the player has an opened [custom menu], even if it's not casted from within the menu itself.  

> **This feature requires either [MythicMobs Premium](/Premium-Features) or [MythicRPG](https://mythiccraft.io/index.php?resources/mythicrpg-spells-classes-professions-more.129/) to be used!**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| slot      | s         | The slot to modify                                                   | 0       |
| icon      | i         | The button to set on the slot                                        | default |


## Examples
```yaml
MyCustomMenu:
  Display: "My Custom Menu"
  Size: 27
  Schema:
    - '0 0 0 0 0 0 0 0 0'
    - '0 0 0 0 B 0 0 0 0'
    - '0 0 0 0 0 0 0 0 0'
  Icons:
    TEST_BUTTON:
      Mapping: B
      Material: GOLD_INGOT
      Model: 4
      Display: 'Test'
      Skills:
      - setcustommenubutton{slot=11;icon=DYNAMIC_BUTTON}
    DYNAMIC_BUTTON:
      Material: IRON_SWORD
      Model: 100
```

<!-- LINKS -->
[custom menu]: /Custom-Menus

<!--TAGS -->
<!--tag:Custom-Menu>
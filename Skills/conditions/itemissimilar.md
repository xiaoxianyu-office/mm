Checks that targeted player's inventory slot if it's similar to an item

**Attributes**

| Attribute | Alias          | Description                                                          | Default |
|-----------|----------------|----------------------------------------------------------------------|---------|
| item      | i, material, m | The item to check for                                                | DIRT    |
| slot      | s              | The inventory slot to check for. Accepts 0 to 35, or equipment slots | HAND    |

---

**Examples**

Tests the item in slot 0, or the first slot, of the targeted player's inventory.
```yml
Conditions:
  - itemissimilar{i=MyCustomItem;slot=0} true
```

**Extra Information:**

- [x] Type: Entity
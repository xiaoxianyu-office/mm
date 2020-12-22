**Description:** This condition checks if the target entity is wearing the selected item.


---

**Attributes:**

| Attribute | Alias     | Description |
| --------- | --------- | ----------- |
| armorslot | slot, s   | The item slot to check. |
| material  | mmitem, m | A material or MythicItem name to check for. |
| checklore | cl        | Whether to strictly match item lore. |

**Valid Slots:**

| HEAD | CHEST | LEGS | FEET | HAND | OFFHAND |       
| ---- | ----- | ---- | ---- | ---- | ------- |  

**Aliases:**

| Condition Aliases |
| ----------------- | 
| iswearing         |
| wielding          |
| iswielding        |
---

**Examples:**

```
Conditions:
- wearing{slot=HAND;m=IRON_SWORD} true
```

---

**Extra Information:**

- [x] Type: Entity
- [x] Added in: 4.5
- [x] Author: jaylawl



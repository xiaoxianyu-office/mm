**Description:** This condition checks if the target entity is wearing the selected item.  

**Type:** Entity

---

**Attributes:**

| Attribute | Alias     | Description |
| --------- | --------- | ----------- |
| armorslot | slot, s   | The item slot to check. |
| material  | mmitem, m | A material or MythicItem name to check for. Also supports MMOItems in the format mmoitems.TYPE.ID |

**Valid Slots:**

| HEAD | CHEST | LEGS | FEET | HAND | OFFHAND |       
| ---- | ----- | ---- | ---- | ---- | ------- |  
---

**Examples:**

```
Conditions:
- wearing{slot=HAND;m=IRON_SWORD} true
- wearing{slot=CHEST;m=mmoitems.TYPE.ID} true
```

---


**Aliases:**

| Condition Aliases |
| ----------------- | 
| iswearing         |
| wielding          |
| iswielding        |
---
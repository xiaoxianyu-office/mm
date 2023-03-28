**Description:** Tests if the target player or an item container has exactly the given number of the given material.

---

**Attributes:**

| Attribute | Alias          | Description                                                                                  | Default |
|-----------|----------------|----------------------------------------------------------------------------------------------|---------|
| item      | i, material, m | A vanilla, or mythicitem, to check for. Can also check for MMOItems using `mmoitems.TYPE.ID` | DIRT    |
| amount    | a              | The number of items to check for                                                             | \>0     |

---

**Examples:**

```yaml
Conditions:
- hasitem{i=stick;amount=>1} true
```
```yaml
Conditions:
- hasitem{i=my_custom_item;amount=<10} true
```
```yaml
Conditions:
- hasitem{i=mmoitems.SWORD.CUTLASS;amount=1to10} true
```

---

**Extra Information:**

- [x] Type: Entity, Location
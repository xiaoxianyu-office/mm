**Description:** Tests if the target player, chest, or shulkerbox has exactly the given number of the given material.

---

**Attributes:**

| Attribute | Alias   | Description | Default |
| --------- | ------- | ----------- | ------- |
| item      | i, material, m | A material to check for. Can also check for MMOItems using `mmoitems.TYPE.ID` | DIRT |
| amount    | a | The number of items to check for | >0 |

---

**Examples:**

```yaml
Conditions:
- hasitem{i=STICK;amount=>1} true
```

```yaml
Conditions:
- hasitem{i=STICK;amount=<10} true
```

```yaml
Conditions:
- hasitem{i=STONE;amount=1to10} true
```



---

**Extra Information:**

- [x] Type: Entity, Location
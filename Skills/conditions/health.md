**Description:** Matches the target's health

---

**Attributes:**

| Attribute | Alias              | Description                   |
| --------- | -------------------| ----------------------------- |
| health    | h, amount, a       | The health range to check for |

---

**Examples:**

```
Conditions:
- health{h=50} true
```

```
# Below 50 health
Conditions:
- health{h=<50} true
```

```
# Above 10 health
Conditions:
- health{h=>10} true
```

---

**Extra Information:**

- [x] Type: Entity
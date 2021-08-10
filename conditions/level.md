**Description:** Checks the target MythicMob's level

---

**Attributes:**

| Attribute | Alias | Description              |
| --------- | ----- | ------------------------ |
| level     | l     | The level range to match |

---

**Examples:**

```
Conditions:
- level{l=10} true
```

```
Conditions:
- level{l=>10} true
```

```
Conditions:
- level{l=1to10} true
```

```
Conditions:
- level{l=<10} true
```

**Extra Information:**

- [x] Type: Entity
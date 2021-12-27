**Description:** Matches a range to how many mobs are in the target world

**Type:** Location

---

**Attributes:**

| Attribute | Alias | Description               | Default |
| --------- | ----- | ------------------------- | ------- |
| amount    | a     | The number range to match | 0 |

---

**Examples:**

```
Conditions:
- mobsinworld{a=20to50} true
```

```
Conditions:
- mobsinworld{a=<50} true
```

---

**Extra Information:**

- [x] Type: Location
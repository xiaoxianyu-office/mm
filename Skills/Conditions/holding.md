**Description:** Checks if the target is holding a given material

**Type:** Entity

---

**Attributes:**

| Attribute | Alias   | Description                |
| --------- | ------- | -------------------------- |
| material  | m       | A material or MythicItem name to check for |

---

**Examples:**

```
# Make sure you use all caps for materials, otherwise the console will say it is not a valid material!
Conditions:
- holding{m=DIAMOND_SWORD} true
```

---

**Extra Information:**

- [x] Type: Entity
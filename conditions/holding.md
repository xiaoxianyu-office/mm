**Description:** Checks if the target is holding a given material

**Type:** Entity

---

**Attributes:**

| Attribute | Alias   | Description                |
| --------- | ------- | -------------------------- |
| material  | m       | The material type to match |

---

**Examples:**

```
# make sure to use ALL CAPS, otherwise the console
# will tell you it is not a valid material!!
Conditions:
- holding{m=DIAMOND_SWORD} true
```
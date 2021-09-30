**Description:** Checks how many mobs are in a given radius

---

**Attributes:**

| Attribute | Alias | Description                    |
| --------- | ----- | ------------------------------ |
| types     | type, t     | The types of mobs to check for |
| amount    | a     | The range of mobs to check for |
| radius    | r     | The radius to check            |

---

**Examples:**

```
Conditions:
- mobsInRadius{types=NewZombie;amount=5to10;radius=15}
```

---

**Extra Information:**

- [x] Type: Location
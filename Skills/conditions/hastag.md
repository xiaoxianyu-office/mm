**Description:** Tests if the target has a scoreboard tag

---

**Attributes:**

| Attribute | Alias   | Description          |
| --------- | ------- | -------------------- |
| tag       | t       | The tag to check for |

---

**Examples:**

```
Conditions:
- hastag{t=KilledBoss1} true
```

```
TargetConditions:
- hastag{t=PuzzleRoom1Solved} true
```

---

**Extra Information:**

- [x] Type: Entity
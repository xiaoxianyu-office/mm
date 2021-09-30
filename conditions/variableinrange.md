**Description:** Checks if the given numeric variable is within a certain range.

---

**Attributes:**

| Attribute | Aliases        | Description               |
| --------- | -------------  | ------------------------- |
| variable | name, n, key, k | Variable to match |
| value| val, v| A number range to match|

---

**Examples:**

```
  Conditions:
  - variableInRange{var=caster.Cooldown;value=<0.01} cancel
  Skills:
  - setvariable{var=caster.Cooldown;type=float;value="10"}
  - message{m="&7Cooldown over!"}
```

---

**Extra Information:**

- [x] Type: Skill
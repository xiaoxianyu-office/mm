**Description:** Checks the MythicMob type of the target mob

---

**Attributes:**

| Attribute | Aliases    | Description               |
| --------- | -------- | ------------------------- |
| type      | types, t | A list of MythicMob types |

---

**Examples:**

```
Conditions:
- mythicmobtype{t=CoolZombie,IceZombie,SnowZombie} true
```

```
TargetConditions:
- mythicmobtype{t=HotZombie,LavaZombie,FireZombie} true
```

---

**Extra Information:**

- [x] Alias: mmtype
- [x] Type: Entity
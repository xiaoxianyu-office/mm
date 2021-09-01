**Description:** Checks the MythicMob type of the target mob

---

**Attributes:**

| Attribute | Alias    | Description               |
| --------- | -------- | ------------------------- |
| type      | types, t | A list of MythicMob types, Can be set to "ANY" |

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

- [x] Type: Entity
**Description:** checks the cause of the damage taken

---

**Attributes:**

| Attribute  | Alias | Description                  |
| ---------- | ----- | ---------------------------- |
| cause      | None  | the cause type of the damage |

---

**Examples:**

```
Conditions:
- damagecause{cause=ENTITY_ATTACK} true
```

List of damage causes: https://hub.spigotmc.org/javadocs/spigot/org/bukkit/event/entity/EntityDamageEvent.DamageCause.html

---

**Extra Information:**

- [x] Type: Entity
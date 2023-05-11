**Description:** Tests the entity type of the target
List of types can be found here:
https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
---

**Attributes:**

| Attribute | Alias    | Description                     |
| --------- | -------- | ------------------------------- |
| type      | types, t | A list of entity types to match |

---

**Examples:**

```
Conditions:
- entitytype{t=ZOMBIE} true
```

```
TargetConditions:
- entitytype{t=WITCH} true
```

```
TriggerConditions:
- entitytype{t=PLAYER} true
```

---

**Extra Information:**

- [x] Type: Entity
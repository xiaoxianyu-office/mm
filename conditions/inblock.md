**Description:** Checks the material at the target location
---

**Attributes:**

| Attribute | Alias     | Description               |
| --------- | --------- | ------------------------- |
| block     | blocks, b | A list of blocks to match |

---

Valid for any Bukkit material type.

https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html

---

**Examples:**

```
Conditions:
- inblock{b=WATER,LAVA} false
```

---

**Extra Information:**

- [x] Type: Entity
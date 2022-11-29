**Description**: Matches the number of players in the caster's world

---


**Attributes**

| Attribute | Alias       | Description                                                                                     | Default |
|-----------|-------------|-------------------------------------------------------------------------------------------------|---------|
| amount |   | The number of players to check for. Can be a range |     |

Examples
---
```yaml
Conditions:
  - playersInWorld{amount=>5}
```
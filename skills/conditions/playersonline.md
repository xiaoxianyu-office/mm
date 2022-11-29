**Description**: Matches the number of players online

---


**Attributes**

| Attribute | Alias       | Description                                                                                     | Default |
|-----------|-------------|-------------------------------------------------------------------------------------------------|---------|
| amount |   | The number of players to check for. Can be a range |     |

Examples
---
```yaml
Conditions:
  - playersOnline{amount=>5}
```
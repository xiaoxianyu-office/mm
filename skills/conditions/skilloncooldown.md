**Description**: Checks if the given skill is in cooldown for the target

---


**Attributes**

| Attribute | Alias       | Description                                                                                     | Default |
|-----------|-------------|-------------------------------------------------------------------------------------------------|---------|
| skill |   | The metaskill to check |     |

Examples
---
```yaml
TargetConditions:
  - skillOnCooldown{skill=TestSkill}
```
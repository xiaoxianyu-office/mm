Mechanic: Set Skill Cooldown
--------------------------
Sets the given metakill's cooldown to the given value (in seconds)

**Attributes**

| Attribute | Alias | Description |
| --------- | ----- | ----------- |
| skill     |       | The metaskillset of which you want to set the cooldown       |
| seconds   |       | The duration of the cooldown |

Examples
--------
this example would set the cooldown of the metaskill *test_skill* to 10 seconds for the caster
```
- setSkillCooldown{skill=test_skill;seconds=10} @self

```
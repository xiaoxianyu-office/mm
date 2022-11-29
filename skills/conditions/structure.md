**Description**: Matches if the target location is inside of a structure. Supports wildcards and structures from datapacks.

---


**Attributes**

| Attribute | Alias       | Description                                                                                     | Default |
|-----------|-------------|-------------------------------------------------------------------------------------------------|---------|
| structure |  s         | The structure to check for.|      |


Examples
---
```yml
Conditions:
  - structure{s=minecraft:desert_pyramid} true
```
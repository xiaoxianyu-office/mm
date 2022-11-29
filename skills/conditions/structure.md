**Description**: Matches if the location is located inside of a structure. Supports wildcards and structures from datapacks.

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
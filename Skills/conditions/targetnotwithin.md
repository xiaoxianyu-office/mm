**Description:** Tests if the target's target is not within a certain distance.
---

**Attributes:**

| Attribute | Aliases        | Description               |
| --------- | -------------  | ------------------------- |
| distance | d | The distance to match |

As of July 4th 2022 this has been tested and seems to only be working from mobs, not from players! - tested by Rhikcyn with the guidance of Akim91

---

**Examples:**

```
  Conditions:
  - targetnotwithin{d=5} true
```
**Description:** Checks how many players are in a radius.

---

**Attributes:**

| Attribute | Aliases        | Description               | Default |
| --------- | -------------  | ------------------------- | ------- |
| amount | a | the given range value to check | >0 |
| radius | range, r | the given radius to check | 32 |

Example
------

```
Conditions:
- playersinradius{a=>3;r=16}
```

Extra Information
----------

- [x] Alias: pir, playerinradius
- [x] Type: Location
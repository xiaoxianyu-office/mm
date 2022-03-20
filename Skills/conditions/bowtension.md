Checks the bow tension of when an entity shoots from a bow

**Attributes**

| Attribute | Alias       | Description                                                                                     | Default |
|-----------|-------------|-------------------------------------------------------------------------------------------------|---------|
| force     | f, value, v | The value of the force/tension to check for. Accepts ranged values, but only limited to 0 to 1. | >0      |

---

**Examples**

```yml
Conditions:
  - bowtension{value=>0.5} true
```

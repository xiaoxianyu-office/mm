**Description**: sets the probability of the metaskill being executed.

---


**Attributes**

| Attribute | Alias       | Description                                                                                     | Default |
|-----------|-------------|-------------------------------------------------------------------------------------------------|---------|
| chance     |   | The floating value which denotes the chance. It can range between 0 and 1, with 0 being a 0% chance and 1 being a 100% chance|       |

---

**Examples**

In this example, the metaskill will be executed only 30% of the times it has been triggered, on average.
```yml
Conditions:
  - chance{chance=0.3} true
```
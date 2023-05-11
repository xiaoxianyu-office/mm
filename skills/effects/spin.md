**Description:** 

Causes the target entity to spin around for the given duration.

---

**Attributes:**

| Attribute        | Alias | Description                                                   | Default Values |
| ---------------- | ----- | ------------------------------------------------------------- | -------------- |
| duration         | d     | How long (in ticks) the target entity should spin             | 40             |
| velocity         | v     | The velocity the target spins at                              | 18             |

---

**Examples:**

```
- effect:spin{duration=100;velocity=20} @self
```

**Note:**

When you set velocity to 0,this mob's direction will be locked.

When a mob casts the spin mechanic repeatedly it will move upwards while spinning.
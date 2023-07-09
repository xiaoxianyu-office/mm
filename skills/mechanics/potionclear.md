Clears all potion effects from the target entity

**Attributes**

| Attribute | Alias | Description |
| --------- | ----- | ----------- |
| types      | type  | The type or list of types of potion effect to clear.        |

Not providing a type will clear all effects.

**Examples**

```yaml
- potionclear{type=FIRE_RESISTANCE} @target
- potionclear{type=FIRE_RESISTANCE,SPEED} @self
- potionclear{} @self
```
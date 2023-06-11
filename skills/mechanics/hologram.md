Spawns a hologram at a target location.

**Attributes**:
---------------

| Attributes | Alias |    Description   |     Default Value     |
| ---------- | ----- | ---------------- | --------------------- |
|    text    | t     | The text to show | Hologram Text Missing |
|    stay    | time  | The duration of the hologram in ticks | 100 |

**Example**:
-----------
Creates a hologram above the mob when the mob gets right clicked, which displays for 100 ticks.
```yaml
    Skills:
    - holo{text="Example Text";time=100} @selflocation{y=1.6} ~onInteract
```
**Extra Information**:
---------------------

- [x] Aliases: summonhologram, holo
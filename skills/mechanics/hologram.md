Spawns a hologram at a target location.

**Attributes**:
---------------

| Attributes | Alias |    Description   |     Default Value     |
| ---------- | ----- | ---------------- | --------------------- |
|    text    | t     | The text to show | Hologram Text Missing |
|    stay    | time  | hologram's stay time(ticks) | 100 |

**Example**:
-----------

    Skills:
    - holo @selflocation{y=1.6} ~onInteract

**Extra Information**:
---------------------

- [x] Aliases: summonhologram, holo
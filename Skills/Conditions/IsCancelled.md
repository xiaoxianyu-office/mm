## Description
Checks whether the triggering event is currently cancelled.

This is true when a prior mechanic in the skill chain has cancelled the event (for example via `cancelevent`), or when the underlying Bukkit event reports itself as cancelled. It is most useful for mid-chain checks in trigger flows such as `~onDamaged`, after another mechanic may have cancelled the event.


## Attributes
| Attribute | Aliases             | Description                          | Default |
|-----------|---------------------|--------------------------------------|---------|
| value     | val, v, boolean, bool, b | The cancelled state to match against | true    |


## Examples
```yaml
  Conditions:
  - iscancelled{value=true} true
```


## Aliases

- [x] isCanceled
- [x] cancelled
- [x] canceled

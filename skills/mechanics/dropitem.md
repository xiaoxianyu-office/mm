===================

Drops a set of items or optionally a
[DropTable](/databases/drops/overview).

Attributes
----------

| Attribute | Aliases | Description                                                            | Default Value |
|-----------|---------|------------------------------------------------------------------------|---------------|
| items     | i       | Items to drop. Can be a comma-separated list of items, or a DropTable. | NONE          |

  

Examples
--------
Example of dropping specific items.
```yaml
Skills:
  - dropitem{i=diamond_sword,diamond} @self ~onDeath
  - ...
```
Example of dropping items from a DropTable.
```yaml
Skills:
  - dropitem{i=SkeletonKingDrops} @self ~onSpawn
  - ...
```
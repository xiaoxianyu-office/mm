## Description
Drops a set of items or optionally a
[DropTable](/databases/drops/overview).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| items     | i       | Items to drop. Can be a comma-separated list of items, or a DropTable. You can specify an amount by putting a space and a number after the item name. | NONE    |


## Examples
Example of dropping specific items.
```yaml
  Skills:
  - dropitem{i=diamond_sword,diamond} @self ~onDeath
  - ...
```
The below example will drop a Diamond Sword and 5 Diamonds
```yaml
  Skills:
  - dropitem{i=diamond_sword,diamond 5} @self ~onDeath
  - ...
```
##
Example of dropping items from a DropTable.
```yaml
  Skills:
  - dropitem{i=SkeletonKingDrops} @self ~onSpawn
  - ...
```
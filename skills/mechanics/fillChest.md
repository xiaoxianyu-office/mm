Mechanic: Fill Chest
===================

Fills a chest with a list of items, or a [droptable](Items/Drops#drop-tables)

Attributes
----------

| Attribute | Aliases | Description                                                            | Default Value |
|-----------|---------|------------------------------------------------------------------------|---------------|
| items     | i       | Items to fill a chest with. Can be a comma-separated list of items, or a DropTable. | NONE          |
| shouldStack |       | Should the given items stack if possible. true/false                   |         |
| shouldempty | empty | Should the container be emptied before the items are added. true/false |         |


  

Examples
--------

Example of filling a chest with specific items.

      Skills:
      - fillchest{i=diamond_sword,diamond} @Location{x=#;y=#;z=#} ~onDeath

Example of filling a chest with a droptable.

      Skills:
      - fillchest{i=SkeletonKingDrops} @Location{x=#;y=#;z=#} ~onSpawn
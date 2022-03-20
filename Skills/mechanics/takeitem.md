Mechanic: TakeItem
=================
*Aliases*: take, itemtake, takeitems

Removes an item from the target

Attributes
----------

| Attribute | Aliases        | Description                      | Default |
|-----------|----------------|----------------------------------|---------|
| item      | material, m, i | The item, or material, to remove | DIRT    |
| amount    | a              | The amount to remove             | 1       |


Examples
--------

Would remove a stack of dirt from the nearest player's inventory
```yml
Skills:
  - takeitem{i=DIRT;a=64} @NearestPlayer{r=10}
```
      
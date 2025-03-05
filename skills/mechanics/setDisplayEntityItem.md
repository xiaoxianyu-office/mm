## Description
Sets the item component of Item Display entities


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| item      | i, type, t, material, mat, m | The item to use. If not set, the mechanic will remove the item from the entity instead | AIR<!--type:Item--> |


## Examples
```yaml
ExampleMob:
  Type: ITEM_DISPLAY
  Skills:
  - setDisplayEntityItem{i=MyMythicItem} @self ~onSpawn
```


<!--TAGS-->
<!--tag:Item-->

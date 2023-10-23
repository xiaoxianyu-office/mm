## Description
Makes an elytra-equipped entity glide or stop gliding. This only works
on players or entities that have elytra equipped in the chestplate slot.
The targeted entity also has to be in the air at the time!


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| gliding   | g         | If the entity is forced to glide or not                              | true    |


## Examples
This example will make the mob glide if it has elytra equipped and is in the air at the time.
```yaml
MakeMobGlide:
  Skills:
  - setgliding{g=true} @self
```
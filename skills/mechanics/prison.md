## Description
Encases the target entity inside a temporary prison of blocks. The
created blocks will disappear automatically after the specified
duration.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m, t, type | The Material (block type) the prison is made out of.                | ICE<!--type:Material--> |
| duration  | d         | How long (in ticks) the prison will last                             | 100     |
| breakable | b         | (true/false) Whether or not the prison blocks can be broken.         | false   |
| materialdata | md     | Deprecated. The data of the material, which existed in older versions of the game. If present, the plugin will try to convert the material to its new equivalent            | 0       |


## Examples
This skill creates a iron block prison around the target of the casting
mob, for 200 ticks (10 seconds), and the prison can be mined.
```yaml
IronPrison:
  Skills:
  - prison{material=IRON_BLOCK;duration=200;breakable=true} @target
```


<!--TAGS-->
<!--tag:World-->

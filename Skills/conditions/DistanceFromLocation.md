## Description
Checks if the target is within a certain distance of a specified location


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| x         |           | The x component of the location                                      | 0       |
| y         |           | The y component of the location                                      | 0       |
| z         |           | The z component of the location                                      | 0       |
| world     | w         | The world of the location. Defaults to the world of the target       |         |
| distance  | d         | The distance from the specified location to check against            |         |


## Examples
```yaml
  TargetConditions:
  - distanceFromLocation{x=10;y=20;z=30;distance=<20} true
```
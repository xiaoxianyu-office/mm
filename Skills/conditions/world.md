## Description
Checks the name of the target world.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| world     | w         | A list of worlds you wish to check for                        | tutorial_world |


## Examples
```yaml
  Conditions:
  - world{w=tutorial_world} true
```
```yaml
  Conditions:
  - world{w=world1,world2} true
```
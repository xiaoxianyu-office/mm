## Description
Matches if the target location is inside of a structure. Supports wildcards and structures from datapacks.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| structure | structures, s | The structure to check for. Can be a list.                       | village |


## Examples
```yml
  Conditions:
  - structure{s=minecraft:desert_pyramid} true
```
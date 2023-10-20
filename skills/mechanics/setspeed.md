===================

## Description:

Causes the target to change its speed attribute

## Attributes:

| Attributes | Description                             | Default Value |
|------------|-----------------------------------------|---------------|
| speed      | Speed of the entity                     | 1             |
| type       | Type of speed, can be WALKING or FLYING | WALKING       |


## Examples:

This will set the mob's walking speed to 2 when it spawns
```yaml
Skills:
  - setspeed{speed=2;type=walking} ~onSpawn
```
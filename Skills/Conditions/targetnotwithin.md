## Description
Tests if the target's target is not within a certain distance.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  | d         | Distance to check                                                    | 0       |


## Examples
```yaml
  Conditions:
  - targetnotwithin{d=10} true
```
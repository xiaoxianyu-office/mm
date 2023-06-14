## Description
Tests if the target's target is within a certain distance.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  | d         | Distance to check                                                    | 0       |


## Examples
```yaml
  Conditions:
  - targetwithin{d=10} true
```
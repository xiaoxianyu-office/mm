## Description
Checks if the distance between the caster and its tracked location is within the specified values


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| distance  | d         | The values to check for. Can be a range.                             |         |


## Examples
```yml
Conditions:
  - DistanceFromTrackedLocation{d=5} true
```
```yml
Conditions:
  - DistanceFromTrackedLocation{d=2to10} true
```

## Aliases
- [x] distanceFromTL
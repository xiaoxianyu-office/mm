## Description
Tests whether the target is inside an axis-aligned bounds box defined by two opposite corners. Corner coordinates support placeholders and math expressions.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| corner1   | c1        | First corner of the box. A pin name, `world,x,y,z`, or `x,y,z`.      |         |
| corner2   | c2        | Second corner of the box. A pin name, `world,x,y,z`, or `x,y,z`.     |         |

When a corner is given as `x,y,z` (no world), the world of the checked location is used.


## Examples
```yaml
  Conditions:
  - inBounds{c1=-10,60,-10;c2=10,80,10} true
```

```yaml
  TargetConditions:
  - inBounds{corner1=world,0,64,0;corner2=world,32,96,32}
```

```yaml
  Conditions:
  - inBounds{c1=mypin;c2=anotherpin} true
```


## Aliases
- [x] withinBounds
- [x] insideBounds

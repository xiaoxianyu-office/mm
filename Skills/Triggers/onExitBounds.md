## Description
This Trigger has a special syntax: `~onExitBounds{corner1=<corner>;corner2=<corner>}`

Executes the skill when the mob moves out of the axis-aligned region defined by two corners. The mob's position is checked on its timer clock (the same clock that drives [onTimer](/Skills/Triggers/onTimer)), and the skill fires once when the mob crosses out of the region, not repeatedly while it stays outside.

Each corner accepts a pin name, `world,x,y,z`, or `x,y,z` (the world of the mob's location is used for the three-value form). Coordinate values support placeholders and math expressions. Both corners must be in the same world, and both `corner1` and `corner2` are required.

> The associated [@trigger](/Skills/Targeters/Trigger) is the mob itself


## Attributes
| Attribute | Aliases | Description                                                        | Default |
|-----------|---------|-------------------------------------------------------------------|---------|
| corner1   | c1      | First corner of the region, as a pin name, `world,x,y,z`, or `x,y,z` | NONE    |
| corner2   | c2      | Second corner of the region, as a pin name, `world,x,y,z`, or `x,y,z` | NONE    |


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world
    # when the mob leaves the region between the two corners
    - message{m=Left the arena} @World ~onExitBounds{corner1=world,100,64,100;corner2=world,120,80,120}
```


## Aliases
- [x] onExit_Bounds
- [x] onLeaveBounds
- [x] onLeave_Bounds
- [x] onBoundsExit
- [x] onBounds_Exit

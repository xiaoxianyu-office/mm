## Description
This Trigger has a special syntax: `~onEnterBounds{corner1=<corner>;corner2=<corner>}`

Executes the skill when the mob moves into the axis-aligned region defined by two corners. The mob's position is checked on its timer clock (the same clock that drives [onTimer](/Skills/Triggers/onTimer)), and the skill fires once when the mob crosses into the region, not repeatedly while it stays inside. A mob that spawns already inside the region fires this trigger on its first check.

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
    # when the mob walks into the region between the two corners
    - message{m=Entered the arena} @World ~onEnterBounds{corner1=world,100,64,100;corner2=world,120,80,120}
```


## Aliases
- [x] onEnter_Bounds
- [x] onBoundsEnter
- [x] onBounds_Enter

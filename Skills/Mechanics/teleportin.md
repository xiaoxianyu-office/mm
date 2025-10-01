## Description
Will teleport the target relative to the caster's yaw. The direction attribute must be in this format: direction=x,y,z

`x` is forward or backward, `y` is up or down, and `z` is left or right

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| vector    | direction,dir,d,v | The direction to where the mob will be teleported            |         |
| yaw       | y         | Yaw modifier                                                         | 0       | 
| targetasorigin | tao  | Will use the target's location as the origin instead of the caster's | false   |
            
    
## Examples
Will teleport the player that triggered the skill to the right of the caster.
```yaml
  Skills:
  - teleportin{vector=0,0,1} @trigger ~onInteract
```

## Aliases
- [x] tpin 
- [x] tpdir 
- [x] tpi


<!--TAGS-->
<!--tag:Movement:Teleport-->

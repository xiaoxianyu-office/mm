## Description
Holds the target in place temporarily.

> [!warning]
> This mechanic can cause Spigot to kick the player (`PlayerName moved wrongly!`)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stopai    | ai        | Removes entity AI while stunned                                      | false   |
| gravity   | g         | Remove gravity from target when stunned (1.9+)                       | false   |
| facing    | face, f   | When false, entity cannot rotate or look around when stunned         | false   |
| noknockback | nokb, kb | When true, entity cannot be knocked back when stunned               | false   |


## Examples
Stuns the target for 3 seconds, during which the target cannot rotate.
```yaml
ExampleSkill:
  Skills:
  - aura{d=60;components=[
    - stun{f=false}    
    ]} @target
```


## Aliases
- [x] stunned


<!-- LINKS -->
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:AI-->
<!--tag:Movement-->


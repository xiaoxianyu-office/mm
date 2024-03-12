## Description
Forces the entity to play an animation


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| animation | a, effect, e | The animation to play                                             | 1       |
| audience  |           | The [audience] of the effect                                         | world   |

### Animation Attribute
| ID    | Animation               |
|-------|-------------------------|
| 0     | Swing main arm          |
| 1     | Take damage             |
| 2     | Leave bed               |
| 3     | Swing offhand           |
| 4     | Critical effect         |
| 5     | Magic critical effect   |


## Examples
Causes the caster to swing their arm.
```yaml
SwingSkill:
  Skills:
  - playanimation{a=0;audience=World} @Self
```


## Aliases
- [X] effect:playanimation
- [X] e:playanimation
- [x] playarmanimation
## Description
Sets the given metakill's cooldown to the given value (in seconds)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| skill     | s   | The [metaskill] of which you want to set the cooldown. Defaults to the executing one |
| seconds   | sec, time, t | The duration of the cooldown                                      | 0       |


## Examples
```yaml
  Skills:
  - setSkillCooldown{skill=test_skill;seconds=10} @self
```
> This example would set the cooldown of the metaskill *test_skill* to 10 seconds for the caster


## Aliases
- [x] skillCooldown
- [x] setskillcd
- [x] skillcd


<!-- ALIASES -->
[metaskill]: /Skills/Metaskills
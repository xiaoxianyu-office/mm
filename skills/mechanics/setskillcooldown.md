## Description
Sets the given metakill's cooldown to the given value (in seconds)

> If used to set the cooldown of the metaskill the mechanic is in a delay of at least `0` between the execution of the metaskill and the mechanic must be used


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| skill     | s   | The [metaskill] of which you want to set the cooldown                      |         |
| seconds   | sec, time, t | The duration of the cooldown                                      | 0       |


## Examples
```yaml
  Skills:
  - setSkillCooldown{skill=test_skill;seconds=10} @self
```
> This example would set the cooldown of the metaskill *test_skill* to 10 seconds for the caster

##
```yaml
ExampleSkill:
  Cooldown: 0
  OnCooldownSkill: ExampleSkill-DisplayCooldown
  Skills:
  - delay 0
  - setSkillCooldown{s=ExampleSkill;seconds=<skill.cooldown>/20} @self
```
> How to use the mechanic if you intend to set the cooldown of the calling metaskill


## Aliases
- [x] skillCooldown
- [x] setskillcd
- [x] skillcd


<!-- ALIASES -->
[metaskill]: /Skills/Metaskills
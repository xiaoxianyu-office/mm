## Description
Executes the skill when the mob hears a sound, [if this feature has been enabled](/Mobs/Mobs#hearing).  
The `<skill.var.volume>` [placeholder](/Skills/Placeholders#variable-placeholders) can be used in the triggered skill to return a float value between 1 and 15 representing the distance from the sound source

> The associated [@trigger](/Skills/Targeters/Trigger) is the entity that generated the sound  

> The associated [@origin](/Skills/Targeters/Origin) is the location where the sound was generated  

| [Implemented Placeholders](/Skills/Placeholders#variable-placeholders)     |
|--------------------------------|
| `<skill.var.volume>`           |
| `<skill.var.sound-type>`       |


## Examples
```yaml
ICanHearYou:
  Type: ZOMBIE
  Hearing:
    Enabled: true
  Skills:
  - message{m="I can hear you <trigger.name>! <skill.var.volume>? Way too loud!"} @trigger ~onHear
```


## Aliases
- [x] onVibration
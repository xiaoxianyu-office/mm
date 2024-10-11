## Description
Sets the "stance" attribute of the target Mythic Mob to the given
string. Does nothing if the target is not a Mythic Mob.  

This can be used in conjunction with the [Stance condition](/skills/conditions/stance) to create different stances or phases
for a mob, where they use different abilities.  
The stance condition will match the current stance loosely, meaning if you set the stance to
"angry fiery explosive" the stance condition will be true for the stance
"fiery".


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| stance    | s         | The string-name of the stance                                        | default |


## Examples
This skill would change the caster's phase to "bowphase"
```yaml
StanceChangeSkill:
  Skills:
  - setstance{stance=bowphase} @self
```


This skill would only be usable when the caster had the stance
"bowphase"
```yaml
AnotherSkill:
  Conditions:
  - stance bowphase
  Skills:
  - ...some bow skills
```


## Aliases
- [x] stance
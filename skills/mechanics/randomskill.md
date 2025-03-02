## Description
Executes a random skill from the list of supplied [skills](/skills/mechanics/skill). Will ignore any skills that are on cooldown or whose conditions do not check. There is no limit to how many skills can be added.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| skills    | s,  m, meta, metas  | The list of skills to execute, must be separated by a `,`  |<!--type:Metaskill-->|
| fallbackskill | fbskill, fbs | the metaskill to run if condition checks fail for all skills in the randomskill list |<!--type:Metaskill-->|

## Weight
You can also make your skills be executed with different chances via the weight system by simply adding a space and a number after the skill names. Skills without a weight will default to weight 1. The higher the number the higher chance that skill has for being picked.

In this example SkillOne will have the highest chance of being picked, then SkillFour since it has the default weight of 1, then SkillTwo with its weight of 0.5 and, lastly, SkillThree will have the lowest chance.
```yaml
Skills:
- randomskill{skills=SkillOne 10,SkillTwo 0.5,SkillThree 0.1,SkillFour}
```

## Examples
```yaml
Skills:
- randomskill{skills=skill1,skill2,skill3}
```
Having problems overviewing your randomskill-syntax? Try this:
```yaml
Skills:
- randomskill{
    skills=
    superskill,
    green_skill,
    skill3,
    grandSkill,
    7331
    }
```
Random Skills can be done fully In-Line too!
```yaml
Skills:
- randomskill{skills=
    [- message{m="&7Pleasant afternoon we're having!"} @trigger],
    [- message{m="&7A nice sunny afternoon."} @trigger],
    [- message{m="&7Good Afternoon <trigger.name>! Good to see you!"} @trigger]} @trigger
```


## Aliases
- [x] randommeta


<!--TAGS-->
<!--tag:Random-->
<!--tag:Meta-Mechanic-->
## Description
Cast is an [Aura] mechanic similar to
[Skill](/skills/mechanics/skill) in that it executes a skill, however
Cast instead "casts" the skill similar to how you'd expect an RPG hero
or monster to do so. Cast will execute the given skill if the cast
completes successfully (e.g. if the aura finishes normally), but can be
interrupted.

Only one spell can be cast at a time, and which runs as an aura on the
caster named **#casting**. Removing the aura from the entity will
interrupt the cast. Any aura settings that cause the cast to stop early
will also interrupt casting, such as cancelling on move or teleport.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onCastSkill | oncast, oc | Skill to execute if the cast finishes successfully                   |      |
| onInterruptedSkill | oninterrupted, oninterrupt, oi | Skill to execute if the cast is interrupted |    |
| onNoTargetSkill | onnotargets, onnotarget, ont | Skill to execute if no target is found      |         |
| skillname | spellname, sn | Display name of the spell in the cast bar                        |         |
| showCastBar | castbar, cb | Whether to show the cast bar                                     | true    |
| cancelOnMove | com    | Whether to cancel the aura if the caster moves                       | false   |
> This mechanic inherits every attribute of the [Aura] mechanic
>> - The `auraName` attribute is **set** at `#casting` and **cannot be changed**
>> - The `charges` attribute is **set** at `1` and **cannot be changed**
>> - The `maxStacks` attribute is **set** at `1` and **cannot be changed**
>> - The `mergeAll` attribute is **set** at `true` and **cannot be changed**


## Examples
```yml
myCoolMob:
  Type: ZOMBIE
  Skills:
    - cast{
          skillName="&aFrost Blast";
          duration=40;
          onCast=FrostBlast-Cast;
          onTick=FrostBlast-Tick;
          onInterrupted=FrostBlast-Interrupted;
          onNoTargets=FrostBlast-NoTargets;
          cancelOnMove=true;
          showCastBar=true
        } @target ~onTimer:100
```


<!-- LINKS -->
[aura]: /skills/mechanics/aura
In-Line conditions can be used on individual mechanics and targeters to save you from having to create an entire metaskill for more basic things and to give you more flexibility inside existing metaskills. You can use standard Conditions to check against the caster, TriggerCondtions to check against the trigger, and TargetConditions to check against the target.

In-Line conditions can be used in mob files, skills files and if you have Crucible, they can be used in item files too.

[[_TOC_]]

# Conditions

These conditions will check against the caster itself, they go at the end of a mechanic line and begin with `?`. In the below example the message will only be sent if it is currently raining.
```yaml
SkeletalKnight:
  Type: WITHER_SKELETON
  Skills:
  - message{m="You hit me in the rain?"} @trigger ~onDamaged ?raining
```

For the condition to be true, you can use `?` and for the condition to be false you use `?!`
- `?raining` - True, if it *is* raining
- `?!raining` - False, if it is *not* raining

# TriggerConditions

You can also check against the trigger of the mechanic. It is the same process as above but you use a `~` after the ?. The below example will only send a message to the player who hit the mob, if that player is holding a wooden sword.
```yaml
SkeletalKnight:
  Type: WITHER_SKELETON
  Skills:
  - message{m="You hit me with a wooden sword?"} @trigger ~onDamaged ?~holding{m=WOODEN_SWORD}
```

Just like the standard conditions, for true you can use `?~` and for the condition to be false you use `?~!`
- `?~holding{m=WOODEN_SWORD}` - True, if the player *is* holding a wooden sword
- `?~!holding{m=WOODEN_SWORD}` - False, if the player is *not* holding a wooden sword

### Multiple Conditions

You are able to use as many In-line Conditions and TriggerConditions as you need in your mechanics. Just remember that *all* conditions have to be met for the mechanic to run, in this below example the message will only be sent if it is raining, *and* night, *and* the player who attacked the mob is holding a wooden sword.

```yaml
SkeletalKnight:
  Type: WITHER_SKELETON
  Skills:
  - message{m="You hit me with a wooden sword? in the rain?? at night???"} @trigger ~onDamaged ?raining ?night ?~holding{m=WOODEN_SWORD}
```


# TargetConditions
**In-Line TargetConditions are Premium Only!**

In-line target conditions allow you to apply conditions to your targeters so that you only target the exact entity / location you are looking for. First lets look at the formatting of it. 

In this example a mob would deal 1 damage to any players within 10 blocks that have the aura ``Plagued`` every second.
```yaml
SkeletalKnight:
  Type: WITHER_SKELETON
  Skills:
  - damage{a=1} @PIR{r=10;conditions=[  - hasaura{aura=Plagued} true ]} ~onTimer:20
```

The spacing is crucial for in-line target conditions. Notice that there is two spaces between ``conditions=[`` and ``- hasaura{aura=Plagued} true``. You need to have that double space there.
Also notice that there is one space from ``true`` to ``]}`` and that space needs to be there as well.

You can also use multiple conditions on a single targeter, there is 2 ways of doing this.

Example of droping down a line and indenting:
```yaml
SkeletalKnight:
  Type: WITHER_SKELETON
  Skills:
  - damage{a=1} @PIR{r=10;conditions=[
                              - hasaura{aura=Plagued} false
                              - haspotioneffect{type=WITHER;d=1to999999;l=0to254} true 
                              ]} ~onTimer:20
```
Note that there is still a space after the true at the end of the second condition.

Example of keeping multiple conditions on one line:
```yaml
SkeletalKnight:
  Type: WITHER_SKELETON
  Skills:
  - damage{a=1} @PIR{r=10;conditions=[  - hasaura{aura=Plagued} true  - haspotioneffect{type=WITHER;d=1to999999;l=0to254} true ]} ~onTimer:20
```
Note that there is two spaces between ``conditions=[`` and the first condition, then there is also two spaces between the first condition and the second condition. Finally there is still one space after the true at the end of the second condition.
## Description
Creates an [aura] that, each tick, checks if a set of conditions is met: If so, the execution of the onStart skill is immediately cancelled. 


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| terminateconditions | conditions, cond, c | The conditions to check against                  |<!--type:Conditions-->|
| deep      |           | Whether the terminable aura, once its conditions have been met, should also stop the execution of the [metaskill] it has been called from                                       | false   |
| onterminate | ox      | The [metaskill] to execute once the onStart is terminated            |<!--type:Metaskill-->|
> This mechanic inherits every attribute of the [aura] mechanic

### Deep Attribute
The deep attribute is quite peculiar: when enabled, other than the onStart metaskill, it makes the terminate aura also affect the metaskill it was originally called from. So, if we had a situation like the following
```yaml
ExampleSkill:
  Skills:
  - terminable{deep=true;...}
  - skill:test1
  - delay 100
  - mechanic2

SecondarySkill:
  Skills:
  - mechanic1
  - delay 200
  - mechanic3
```
Then the `ExampleSkill` and the subsequently called `SecondarySkill` metaskill would be stopped if the terminable aura had its conditions met: so, for example, if the terminable aura stopped the execution after 10 ticks, neither `mechanic2` or `mechanic3` could be triggered  

## Examples
```yaml
  Skills:
  - terminable{
    auraName=exampleAura;
    d=2000;
    conditions=[
      - health{h=<50} true
    ];
    onStart=[
    - state{s=charged_attack}
    - delay 20
    - skill{s=ChargedAttackDamage}
    ];
    onTerminate=[
    - state{s=charged_attack;remove=true}
    - state{s=stunned}
    ]} @self
```


## Aliases
- [x] stoppable
- [x] cancelable
- [x] exit
- [x] terminatable


<!-- LINKS -->
[aura]: /Skills/Mechanics/aura
[metaskill]: /Skills/Metaskills


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
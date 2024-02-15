## Description
Creates an [aura] that, after each mechanic of its onStart [metaskill], checks if a set of conditions is met: If so, the execution of the onStart skill is immediately cancelled. This effectively adds a conditional cancel mechanic after each line of the cascading meta skill.  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| terminateconditions | conditions, cond, c | The conditions to check against                  | null    |
| deep      |           | Whether the terminable aura should continue its check even on the metaskills that are called by the onStart [metaskill]                                                     | false   |
| onterminate | ox      | The [metaskill] to execute once the onStart is terminated            |         |
> This mechanic inherits every attribute of the [aura] mechanic


## Examples
```yaml
  Skills:
  - terminatable{
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


<!-- LINKS -->
[aura]: Skills/Mechanics/aura
[metaskill]: Skills/Metaskills
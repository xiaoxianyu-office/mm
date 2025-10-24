## Description
Casts a Metaskill that will determine if the condition should check or not. This allows you to apply more complex logic against a given target. The called Metaskill needs to use the [DetermineCondition](/Skills/Mechanics/DetermineCondition) mechanic in order to set/modify whether this condition should check or not.  

<!--extends:mechanic:metaskillmechanic-->

## Attributes
> This condition inherits every attribute of the [Skill](/Skills/Mechanics/Skill) mechanic


## Examples
```yaml
YourNormalMetaskill:
  Conditions:
  - metaskillcondition{skill=metaskillcondition_check;hello=ciao;world=mondo}
  Skills:
  - message{m="Condition Passed"} @self
metaskillcondition_check:
  Conditions:
  - holding{types=stick}
  Skills:
  - log{message=metaskill condition passed with parameters of <skill.test> <skill.aaa>} @self
  - determineCondition{det=true} @self
```


## Aliases
- [x] skillcondition
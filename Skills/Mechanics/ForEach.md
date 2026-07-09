## Description
Executes the specified metaskill *once and separately* for each target of the mechanic. Each metaskill that will be called will have a single entity/location (from among the original targets) as its inherited target.

On each iteration the mechanic sets the skill-scoped variable `<skill.var.index>` on the called metaskill, holding the position of the current target. The count starts at 0 and increases by 1 per target, and is tracked separately for entity targets and location targets. Do not confuse this with forEachValue's `<skill.index>`, which is a different token.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| targettype | targett, tt | Which type of targets this mechanic should iterate on. Can be `ALL`, `ENTITY` or `LOCATION`| ALL<!--type:ALL,ENTITY,LOCATION-->|

> This mechanic inherits every attribute of the [Skill](/skills/mechanics/skill) mechanic


## Examples
```yaml
# Skills file
ExampleForEach:
  Skills:
  - setvariable{var=skill.listuuid;type=LIST;val=""} @self
  - foreach{skill=ExampleSkill} @PIR{r=10;sort=NEAREST}
  - message{m=<skill.var.listuuid>}

ExampleSkill:
  Skills:
  - variableadd{var=skill.listuuid;value=<target.uuid>}
```

## 

```yaml
# Skills file
IndexForEach:
  Skills:
  - foreach{skill=IndexSkill} @PIR{r=10;sort=NEAREST}

IndexSkill:
  Skills:
  - message{m="Target number <skill.var.index>"} @self
```
> Prints "Target number 0" for the nearest target, "Target number 1" for the next, and so on.


<!--TAGS-->
<!--tag:Meta-Mechanic-->
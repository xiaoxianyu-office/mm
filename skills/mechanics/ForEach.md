## Description
Executes the specified metaskill *once and separately* for each target of the mechanic. Each metaskill that will be called will have a single entity/location (from among the original targets) as its inherited target.


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


<!--TAGS-->
<!--tag:Meta-Mechanic-->
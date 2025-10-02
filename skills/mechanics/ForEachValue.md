## Description
Executes the specified metaskill *once and separately* for each value of the specified list/map formatted value. Each metaskill that will be called will have special skill parameters set depending on the iterated value:
- For list-formatted inputs
  - `<skill.value>` for the iterated value
  - `<skill.index>` for the index of the value
- For map-formatted inputs
  - `<skill.key>` for the iterated key
  - `<skill.value>` for the iterated value
  - `<skill.index>` for the index of the key-value pair


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| values    | val, v    | The list or map formatted string to iterate on                       |         |

> This mechanic inherits every attribute of the [Skill](/skills/mechanics/skill) mechanic


## Examples
```yaml
# Skills file
ExampleForEachValue:
  Skills:
  - setvariable{var=skill.listnames;type=LIST;val="Steve,Alex"} @self
  - foreachvalue{skill=ExampleSkill;values=<skill.var.listnames>} @self # Can also directly use the entry1,entry2,entry3... syntax

ExampleSkill:
  Skills:
  - message{m="Found you :D"} @PlayerByName{name=<skill.value>}
```

```yaml
# Skills file
ExampleForEachValueForMap:
  Skills:
  - setvariable{var=skill.mapnames;type=MAP;val="Steve=hello;Alex=1,2,3"} @self
  - foreachvalue{skill=ExampleSkill;values=<skill.var.mapnames>} @self # Can also directly use the key=value;key2=value2... syntax

ExampleSkill:
  Skills:
  - message{m="You have a value of <skill.value>"} @PlayerByName{name=<skill.key>}
```


<!--TAGS-->
<!--tag:Meta-Mechanic-->
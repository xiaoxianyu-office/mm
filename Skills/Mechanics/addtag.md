## Description
Adds a scoreboard tag to the target.

This is used in conjunction with the **hastag condition** (see
[Conditions](/skills/conditions/hastag)). You can also use the vanilla command
`/tag <targets> add <name>` to do the same thing.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| tag       | t         | The string-name of the tag                                           | default |


## Examples
This skill would give the casting mob the tag "Test".
```yaml
TagSkill:
  Skills:
  - addtag{t=Test} @self
```
##
This skill would only run on the mob if it had the tag, "Test".
```yaml
TagTest:
  Conditions:
  - hastag{t=Test}
  Skills:
  - suicide @self
```


## Aliases
- [x] addscoreboardtag
- [x] tagadd


<!--TAGS-->
<!--tag:Scoreboard-->
## Description
Removes a scoreboard tag from the target.

This is used in conjunction with the **hastag condition** (see
[Conditions](/conditions/start)). You can also use the vanilla command
`/scoreboard players tag <player name> remove [Tag Name]` to do
the same thing.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| tag       | t         | The string-name of the tag                                           | default |


## Examples
This skill would give the casting mob the tag "Test".
```yaml
UntagSkill:
  Skills:
  - removetag{t=Test} @self
```


## Aliases
- [x] removescoreboardtag
- [x] tagremove


<!--TAGS-->
<!--tag:Scoreboard-->

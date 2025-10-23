## Description
Removes an aura from the target.  

You can decide if the aura executes its `onEnd` metaskill via the `DoEndSkillOnTerminate` attribute of the [Aura](/skills/mechanics/aura) mechanic.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| auraName  | aura, b, buff, buffname, debuff, debuffname, n, name | The name of the aura      | default |
| stacks    | s                        | The amount of stacks                               | Max stacks |

### Aura Attribute
You can specify `ANY` as the value of the attribute in order to remove every aura on the target


## Examples
```yaml
  Skills:
  - auraremove{aura=Ice;stacks=10} @self ~onTimer:200
```


## Aliases
- [x] removeaura
- [x] removebuff
- [x] removedebuff


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
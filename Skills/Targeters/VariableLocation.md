## Description
Targets the location stored in the specified variable. One such variable can be set via the [SetVariableLocation](/skills/mechanics/setvariablelocation) mechanic.

## Attributes

| Attribute      | Aliases  | Description                                                | Default |
|----------------|----------|------------------------------------------------------------|:-------:|
| variable       | name, n, var, key, k | The name of the variable.                      |         |
| scope          | s        | The scope of the variable. Can optionally be set in the name, using the scope.name syntax                                                                        |         |

## Examples
```yaml
ExampleSkill:
  Skills:
  - setvarloc{var=caster.1;v=@targetlocation} @self
  - particle{y=2} @VariableLocation{var=caster.1}
```

## Aliases
- [x] varLocation
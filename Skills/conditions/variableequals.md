## Description
A condition that checks the value of a [variable](/Skills/Variables).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| variable  | name, n, var, key, k | The name of the variable. Can optionally be prefixed with scope|    |
| value| val, v | The value that the variable must equal to return true. Must be applicable for type or the mechanic will fail. Should be surrounded in double-quotes if using spaces. Value can also include placeholders, even from PlaceholderAPI.                                                        |         |
| scope| s| The [scope](/Skills/Variables#variable-scopes) of the variable, e.g. where the variable is located                                                                                        |<!--type:VariableScope-->|


## Examples
In this example, the target players would only hear growling from any number of nearby bears once every 10 minutes.

```yaml
BearMob:
  Skills:
  - skill:BearGrowl @PlayersInRadius{r=40} ~onTimer:60
```
```yaml
BearGrowl:
  TargetConditions:
  - variableEquals{var=target.heardbear;value="yes"} cancel
  Skills:
  - message{m="&7You hear a growling noise..."}
  - setvariable{var=target.heardbear;value="yes";duration=6000}
```
In this example, the skill would only fire if the global variable “poison_storm” is set to true.
```yaml
PoisonStormDamage:
  Conditions:
  - varEquals{var=global.poison_storm;value="yes"}
  Skills:
  - potion{type=POISON;duration=100}
  - damage{amount=1;ignorearmor=true}
```


## Aliases
- [x] variableeq
- [x] varequals
- [x] vareq
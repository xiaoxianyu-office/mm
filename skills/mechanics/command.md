## Description
Executes a command for each target supplied.

[Color codes](/Skills/Placeholders#color-codes) and [variables](/Skills/Variables) are allowed.  

The command specified will not function correctly if it contains double
quotes " or curly brackets {} and must be substitued with their
respective [message variables](/skills/Placeholders#special-characters).  
That happens because the double
quotes and curly brackets are reserved for MythicMobs itself trying to
read the syntax you supplied.


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| command   | c, cmd    | The command to execute                                               |         |
| asCaster  | ac, caster, sudo, asmob| If true the command will execute from the caster instead of the console. | false   |
| asOp      | op        | Whether to execute the command with all permissions                  | false   |
| asTarget  | at, target, sudotarget| Will execute the command as the targeted entity          |  false  |
| requireTarget | rt    | Only executes if the skill has a target                      | asTarget's value|

  

## Examples

### Correctly written command-skills
```yaml
  Skills:
  - command{c="give <target.name> gold_ingot 20"} @trigger ~onInteract
  - command{c="minecraft:tp <target.name> <mob.uuid>"} @self ~onDamaged
  - command{c="say HELLO <target.name>";asTarget=true;asOp=true} @NearestPlayer{r=10}
```

### Invalid command-skills

The below example(s) won't work because certain symbols haven't been
substituted with message variables.  
```yaml
  Skills:
  - command{c="minecraft:summon Zombie ~ ~ ~ {NoAI:true,CustomName:"Summoned Zombie"}"}
```
> In this specific case, the `~` symbol is a problem: while normally, in vanilla, it would just mean "the position of the one that is executing the command", this is not possible with this specific setup, as it is the console that is executing the command, and as such there is no "position" that can be used. A way to fix this would have been to use the `<caster.l.x>`,`<caster.l.y>` and `<caster.l.z>` placeholders


### Making a player execute a command
This example will execute the "say" commands for the player that interacted with the mob
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - command{c="say <target.name>";asTarget=true;asOp=true} @trigger ~onInteract
```
## Aliases
- [x] cmd


<!--TAGS-->
<!--tag:Meta-->

## Description
Executes a command for each target supplied.

Color codes and variables are allowed. For a list of color codes look
[here](/databases/misc/colorcodes). Variables can be found
[here](/skills/stringvariables).

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
  - command{c="minecraft:summon Zombie ~ ~ ~ <&lc>NoAI:true,CustomName:<&dq>Summoned Zombie<&dq><&rc>"}
  - command{c="minecraft:summon Zombie ~ ~ ~ {NoAI:true,CustomName:<&dq>Summoned Zombie<&dq>}"}
  - command{c="say HELLO <target.name>";asTarget=true;asOp=true} @NearestPlayer{r=10}
```

### Invalid command-skills

The below example(s) won't work because certain symbols haven't been
substituted with message variables.
```yaml
  Skills:
  - command{c="minecraft:summon Zombie ~ ~ ~ {NoAI:true,CustomName:"Summoned Zombie"}"}
```

##

### **Making a player execute a command**
This example will execute the "say" commands for the player that interacted with the mob
```yaml
ExampleMob:
  Type: ZOMBIE
  Skills:
  - command{c="say <target.name>";asTarget=true;asOp=true} @trigger ~onInteract
```

Tutorials
---------

-   [Villager trades using cmd-mechanics by
    Krowerom](https://www.youtube.com/watch?v=p71bl_W3a4I&feature=youtu.be)
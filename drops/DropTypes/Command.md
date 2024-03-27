## Description
When dropped, a command is executed only once by the console, regardless of the amount specified.  
You can use caster-scoped and trigger-scoped placeholders to fetch information from the mob that dropped the command and the entity that killed it respectively.  
A `<drop.amount>` [placeholder](/Skills/Placeholders#misc-placeholders) can instead be used to fetch the original amount.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| command   | cmd, c    | The command to execute                                               |         |
| ascaster  | caster, ac, sudo, asmob | Whether the command should be executed as the mob dropping it, instead of the console | false |
| astrigger | trigger, at | Whether the command should be executed as the trigger of the drop, instead of the console | false |
| asop      | op, operator | Whether the command should be executed with full permissions      | false   |


## Examples
```yaml
  Drops:
  - command{c="say Hello World! I was dropped <drop.amount> times!"} 1-10 1
```


## Aliases
- [x] cmd
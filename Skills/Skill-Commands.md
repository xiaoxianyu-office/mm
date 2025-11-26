Via the use of Skill Commands, you are able to make every metaskill this feature is used on into an executable command

> **This feature requires either [MythicMobs Premium](/Premium-Features) or [MythicRPG](https://mythiccraft.io/index.php?resources/mythicrpg-spells-classes-professions-more.129/) to be used!**

For instance, the following metaskill
```yaml
MyExampleSkills:
  Command:
    Id: skillTest
    Aliases:
    - testSkill
    Completions:
      example:
      - players
  Skills:
  - message{m=<skill.var.example> our hero!} @self
```
Would register the command `/skilltest`, and actually using `/skilltest Seyarada`, it will result in the caster seeing the message `Seyarada our hero!`

When used this way, the metaskills will always have the caster of the command as the inherited target

# Skill Commands Options
The field `Command` allows the metaskill it is used into to be regarded as a command, also enabling all of the relative options

## Id
The name of the command that will be registered

## Aliases
Other valid names that can be used to trigger the related metaskill as a command. For instance, in the example above, using  `/skilltest` or `/testskill` would yield the same result

## Completions
Elements in the command that will be tab completed.  
They work in a key-value pair, where the key is the future name of the skill-scoped variable that will be holding the inputted argument, and the value is a list of valid inputs that will be tab-completed when inputting the key.  
If specific keywords are used, the values can be made to be dynamic depending on the keyword used, as they will get auto-replaced with the actual lists

> Excess non-completion arguments will be stored in the `excessArgs` skill scoped variable<br><skill.var.excessArgs>

### Completions Keywords
| Keyword          | Description                         |
|------------------|-------------------------------------|
| worlds           | Each world in the server            |
| players          | Each player in the server           |
| items            | Every vanilla item                  |
| mythicitems      | Every registered Mythic items       |

```yaml
    Completions:
      target:
      - players
```

# Examples
```yaml
RandomTP:
  Command:
    Id: randomtp
    Aliases:
    - rtp
    - wild
    Completions:
      target:
      - players
  Conditions:
  - hasPermission{p=rtp.use} true "&cYou do not have permission to use that command"
  - holding{m=DIAMOND} true "&cYou can only use this command while holding a diamond"
  Skills:
  - consumeHeldItem # Take away the diamond as payment
  - potion{t=SLOW_FALLING;l=5;d=100;p=false} @self
  - command{c=teleport <skill.var.target> <random.-999to999> 100 <random.-999to999>}
  FailedConditionsSkills:
  - e:p{p=VILLAGER_ANGRY;hs=1;vs=1;a=100} @self
  - s{s=entity.villager.no} @self
```
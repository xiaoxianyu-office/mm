## Description
The SudoSkill mechanic allows you to force the targeted entity to “cast”
a MythicMobs [Metaskill], even if the targeted entity is a player.  
No single mechanics can be used straight: they have to be in a [Metaskill]!  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| setcasterastrigger | cat |Sets the trigger of the called metaskill to the caster of this mechanic|false|
| target    | t         | Sets the inherited targets of the called metaskill to the specified ones | <!--type:Targeter--> |

> This mechanic inherits every attribute of the [Skill](/skills/mechanics/skill) mechanic

### SetCasterAsTrigger Attribute
If `setcasterastrigger` is `true`, the trigger of the skill will be set to
the caster of the sudoskill. Else the trigger is the caster of the
skill.
```yaml
  Skills:
  - SudoSkill{s=SkillName;setcasterastrigger=true}
```


## Examples
```yaml
# Mob File
SudoMonkey:
  Type: villager
  Display: 'a Villager'
  Skills:
  - sudoskill{s=ExampleSudoskill;cat=true} @trigger ~onDamaged
```
```yaml
# Skills file
ExampleSudoskill:
  Skills:
  - arrowvolley{a=20;s=25;v=10;f=50;rd=200} @EIR{r=30}
  - message{msg="Triggername<&co> <trigger.name>"} @world
```
##
This metaskill will make every entity in a 20 block radius from the caster summon a particle effect. Because of the `target` attribute, the inherited target of the metaskill will be the player that is nearest to the caster in a 30 blocks radius
```yaml
ExampleTargetSkill:
  Skills:
  - sudoskill{
    target=@NearestPlayer{r=30};
    s=[
      - effect:particles
    ]} @EIR{r=20}
```


## Aliases
- [x] sudo

[Metaskill]: /Skills/Metaskills


<!--TAGS-->
<!--tag:Meta-Mechanic-->

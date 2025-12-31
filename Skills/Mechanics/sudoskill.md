## Description
The SudoSkill mechanic allows you to force the targeted entity to “cast”
a MythicMobs [Metaskill], even if the targeted entity is a player.  
No single mechanics can be used straight: they have to be in a [Metaskill]!  


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| setcasterastrigger | cat |Sets the trigger of the called metaskill to the caster of this mechanic|false|
| target    | t         | Sets the inherited targets of the called metaskill to the specified ones | <!--type:Targeter--> |
| chained   | chain     | Whether to make each target of the mechanic cast the specified metaskill *sequentially*, each time targeting the previous caster                                        | false   |

> This mechanic inherits every attribute of the [Skill](/skills/mechanics/skill) mechanic

### SetCasterAsTrigger Attribute
If `setcasterastrigger` is `true`, the trigger of the skill will be set to
the caster of the sudoskill. Else the trigger is the caster of the
skill.
```yaml
  Skills:
  - SudoSkill{s=SkillName;setcasterastrigger=true}
```

### Chained Attribute
The single line from earlier is not really enough to fully explain what is going on. So, let us do so it with a practical example.  
Given that:
- `iteration` is a number to keep track of "where we are" on the list of entities to execute the sudoskill on
- `caster` is the caster of the sudoed metaskill at any given iteration
- `target` is the target of the sudoed metaskill at any given iteration

```yaml
  Skills:
  - sudoskill{chained=true;skill=Example} @EIR{limit=3;radius=10}
```
Caster: `Player`
Targets: `Mob_A`, `Mob_B`, `Mob_C`

| Iteration | Caster  | Target |
|-----------|---------|--------|
| 0         | Mob_A   | Player |
| 1         | Mob_B   | Mob_A  |
| 2         | Mob_C   | Mob_B  |

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

## Effect: Guardian Beam
----
Draws a guardian beam between the origin and the target

### Aliases
effect:guardianbeam, e:guardianbeam, guardianbeam, effect:beam, e:beam

### Attributes

| Attribute | Aliases |	Description | Default Value |
|-----------|---------|-------------|---------------|
| duration  | d       | The time (in ticks) that the effect is active | 400 |
| interval  | i       | how often it ticks | 1      |
| startYOffset | syo  | starting y offset of the beam | 1 |
| fromOrigin | fo     | Make the effect start from @origin instead of from @self | false |
| onstartskill | os | Skill to execute when the effect starts | NONE |
| ontickskill | ot | skill to execute each interval tick | NONE |
| onendskill | oe | skill to execute when the effect ends | NONE |

### Examples

    Guardian_Beam:
      Skills:
      - guardianbeam{d=200;i=1;syo=1;fromOrigin=false;oS=AStartingSkill;oT=ATickingSkill;oE=AEndingSkill} @Target ~onTimer:200
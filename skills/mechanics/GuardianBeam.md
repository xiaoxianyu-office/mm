## Description
Draws a guardian beam between the origin and the target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| duration  | d, maxduration, md | The time (in ticks) for which the effect will be active     | 400     |
| interval  | int, i    | How often the effect will tick                                       | 1       |
| startYOffset | syo    | The starting y offset of the beam                                    | 1       |
| fromOrigin | fo       | Whether to make the effect start from the @origin instead of from @self| false |
| onstartskill | onstart, os | Metaskill to execute when the effect starts                     |         |
| ontickskill | ontick, ot | Metaskill to execute each interval tick                           |         |
| onendskill | onend, oe | Metaskill to execute when the effect ends                           |         |


## Examples
```yaml
Guardian_Beam:
   Skills:
   - guardianbeam{d=200;i=1;syo=1;fromOrigin=false;oS=AStartingSkill;oT=ATickingSkill;oE=AEndingSkill} @Target
```


## Aliases
- [X] effect:guardianbeam
- [X] effect:beam
- [X] e:guardianbeam
- [X] e:beam
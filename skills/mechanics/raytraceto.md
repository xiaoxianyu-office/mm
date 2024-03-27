## Description
Traces a ray to the target, like the [Raytrace](/skills/mechanics/raytraceto) mechanic, but with additional attributes regarding the start and end position of the ray. **\[PREMIUM ONLY\]**


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| startyoffset | syo, ystartoffset, ys | The offset on the y axis of the starting point of the ray | 0   |
| targetyoffset| tyo, ytargetoffset, yt| The offset on the y axis of the ending point of the ray | 0     |
| fromorigin| fo        | If they ray should start from the origin of the mechanic             | false   |
| useeyelocation | uel  | If they ray should start from the eye location of the caster         | false   |
| forwardoffset| startfoffset, sfo | The forward offset of the starting point of the ray       | 0       |
| sideoffset| soffset, sso | The side offset of the starting point of the ray                  | 0       |

> This mechanic also uses all [Attributes of the Raytrace Mechanic](/skills/mechanics/raytrace#attributes)


## Examples
```yaml
MyRaytraceToSkill:
  Skills:
  - raytraceto{
      entitySkill=[
        - damage{amount=20}
      ];
      locationSkill=[
        - particles{p=flame;a=20;s=0.2;hS=0.1;vS=0.1}
      ];
      startyoffset=1;
      targetyoffset=1;
      useeyelocation=true
      } @targetlocation ~onUse
```
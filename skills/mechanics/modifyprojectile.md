## Description
Modifies the projectile, missile, or orbital that activated the mechanic.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| trait     | t         | The trait to modify:<br>`INERTIA`, `POWER`, `VELOCITY`, `RADIUS` and `YOFFSET`                                                                                   | `VELOCITY`<!--type:ModifyProjectile_Trait-->|
| action    | a         | The action to perform for modifying the projectile trait:<br>`ADD`, `SET`, `MULTIPLY`                                                                                  | `MULTIPLY`<!--type:ModifyProjectile_Action-->|
| value     |v          | The value to use for the modification                             | 0          |

### Trait Attribute
The possible values are:
- `INERTIA` - The inertia of the [missile].
- `POWER` - The power of the [projectile], [missile], [orbital]
- `VELOCITY` - The power of the [projectile], [missile]
- `RADIUS` - The power of the [orbital]
- `YOFFSET` - The height of the [orbital]


## Examples

In this example when you shoot the projectile you will watch it slow down gradually to a halt. To test this you can cast it using the in game command below after adding it to a skills.yml file.

`/mm test cast TestingModifyProjectile`

```yaml
TestingModifyProjectile:
  Skills:
  - projectile{oT=TMP_oT;i=1;v=8;d=200;mr=100} @forward{f=100;y=0}
TMP_oT:
  Skills:
  - particles{particle=flame;a=2;hs=0;vs=0;s=0;y=0} @origin
  - modifyProjectile{trait=VELOCITY;action=MULTIPLY;value=0.95}
```



[missile]: /skills/mechanics/missile
[projectile]: /skills/mechanics/projectile
[orbital]: /skills/mechanics/orbital


<!--TAGS-->
<!--tag:Meta-->

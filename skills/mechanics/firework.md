## Description
Creates a firework effect at the target.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | The Type of firework. See below for a list.                          | BALL    |
| power     | p, duration, d | The flight duration of the firework.                            | 2       |
| flicker   | f         | Whether to add the flicker effect to the explosion.                  | false   |
| trail     | tr        | Whether to add the trail effect to the firework rocket.              | false   |
| colors    | color, c  | The color of the firework explosion, in RGB or hex                   | #FFFFFF |
| fadecolors| fcolors, fc| The fade colors of the firework explosion, in RBG or hex            | #FFFFFF |

### Type Attribute
The type attribute's value can be one of the following
- `BALL`
- `BALL_LARGE`
- `BURST`
- `CREEPER`
- `STAR`

### Colors Attribute
It has been reported that the firework will display the opposite color than the one specified in the "color" output. If your firework effect seems to be having this problem, try to invert the color attribute.


## Examples
```yaml
  Skills:
  - effect:firework{t=BALL;d=1;f=true;tr=true} @self ~onInteract
```


## Aliases
- [x] fireworks
- [x] effect:firework
- [x] effect:fireworks
- [x] e:firework
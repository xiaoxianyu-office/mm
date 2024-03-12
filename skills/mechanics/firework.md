## Description
Creates a firework effect at the target.


## Attributes

| Attribute  | Aliases | Description | Default Value |
| ------ | ------ | ------ | ------ |
| type | t | The type of firework. See below for a list. | BALL |
| duration | d | The flight duration of the firework. | 2 |
| flicker | f | Whether to add the flicker effect to the explosion. | false |
| trail | tr | Whether to add the trail effect to the firework rocket. | false |
| colors | c | The color of the firework explosion, in RGB or hex | 0,0,0 |
| fadecolors | fc | The fade colors of the firework explosion, in RBG or hex | 0,0,0 |

### Firework Types
- BALL
- BALL_LARGE
- BURST
- CREEPER
- STAR

### Firework Colors
It has been reported that the firework will display the opposite color than the one specified in the "color" output. If your firework effect seems to be having this problem, try to invert the color attribute.

## Examples
```yaml
  Skills:
  - effect:firework{t=BALL;d=1;f=true;tr=true} @self ~onInteract
```
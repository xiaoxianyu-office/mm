## Description
Creates a sphere of particles at the targeted entity or location.

## Attributes
This effect extends the general [Particle Effect](/skills/effects/particles) and uses all attributes from it.

| Attribute | Alias | Description                      | Default Value |
| --------  | ----- | -------------------------------- | ------------- |
| radius    | r     | The radius of the sphere to draw | 5             |

## Examples
```yaml
FlameSphere:
  Skills:
  - effect:particlesphere{particle=flame;amount=200;radius=5} @self
```
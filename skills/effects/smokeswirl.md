## Description
Creates a swirling vortex of smoke at the targeted entity or location.

## Attributes

| Attribute        | Alias | Description                                                   | Default Values |
| ---------------- | ----- | ------------------------------------------------------------- | -------------- |
| duration         | d     | How many [intervals] the swirl will last                      | 6              |
| interval         | i     | How many ticks there are between each pulse of smoke          | 10             |

## Examples

```yaml
SmokeSwirlSkill:
  Skills:
  - effect:smokeswirl{duration=10;interval=10} @TargetLocation
```
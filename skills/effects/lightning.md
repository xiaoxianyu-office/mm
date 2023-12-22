## Description
Will strike a “fake” lightning bolt at the specified target. 

The effect purely cosmetic and it plays the lightning sound effect, but will not cause any kind of damage to the target.

## Attributes

| Attribute       | Alias     | Description                                              | Default Value |
| --------------- | --------- | -------------------------------------------------------- | ------------- |
| localized       | l         | should lightning only be seen/heard by players in radius | false         |
| localizedradius | lr, r     | the radius of the localized effect<br>Only works if localized is set to true!                       | 128           |

## Examples

```yaml
SuperLightningSkill:
  Skills:
  - effect:lightning @target
  - effect:lightning @self
  - effect:lightning{repeat=20;repeatInterval=1} @PIR{r=100}
```
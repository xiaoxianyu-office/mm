## Description

Shows the near world border effect.

**Players must enable Fancy Graphics to see the effect.**

## Attributes

| Attribute | Alias  | Description                                   | Default Value |
| --------- | ------ | --------------------------------------------- | ------------- |
| duration  | d      | The time (in ticks) that the effect is active | 20            |
| cancel    | c      | If true, it stops any existing redscreen      | false         |

## Examples
```yaml
BloodyEffect:
  Skills:
  - effect:bloodyScreen{d=25} @PIR{r=15} ~onTimer:20
```
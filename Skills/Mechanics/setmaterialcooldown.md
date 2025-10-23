## Description
Sets a cooldown on items of a specified material on the target player


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
|  material | mat, m    | The material to set the cooldown to                              | ENDER_PEARL<!--type:Material--> |
| duration  | d         | The duration of the cooldown in ticks                                | 100     |


## Examples
```yaml
  Skills:
  - setmaterialcooldown{m=CHORUS_FRUIT;d=150} @PIR{r=10}
```
## Description
The blockunmask effect is used to revert blockchanges made by the blockmask effect. For instance, this effect can be used in a high radius after a mob has died in order to “clean up” the fake block updates sent. However this is not necessary, because the fake block changes created by the blockmask effect will be reverted if a chunk is reloaded for a player (but will only revert for that player).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| radius    | r         | The radius of the blockunmask effect                                 | 0       |
| shape     | s         | The shape of the effect. `Sphere`/`Cube`                             | SPHERE<!--type:Shape-->|


## Examples
Will forcibly reverse all effects created by the blockmask effect in the specified radius.
```yaml
  Skills:
  - effect:blockunmask{r=30}
```


## Aliases
- [x] effect:blockUnmask
- [x] e:blockunmask


<!--TAGS-->
<!--tag:Effect-->
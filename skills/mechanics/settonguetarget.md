## Description
Sets the tongue target for a frog caster to the target entity.


## Attributes
> *This mechanic has no attribute*


## Examples
Sets the frog's tongue target to the nearest entity when right clicked.
```yaml
MyLovingFrog:
  Type: FROG
  Skills:
  - setTongueTarget @EIR{r=5;limit=1;sort=NEAREST} ~onInteract
```


## Aliases
- [x] tonguetarget

<!--TAGS-->
<!--tag:AI-->
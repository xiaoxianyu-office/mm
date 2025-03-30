## Description
Targets the predicted location at which the caster's top [target](/Skills/Targeters/Target) will be after an amount of ticks has elapsed, based on its current movement speed.  

To do this, in the code itself, a raytrace from the target's position is used, so, for instance, a block will stop the raytrace before it can reach its supposed end point


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| maxdistance | max, distance, d | The maximum distance from the target's current location that the predicted location can be located at. If the predicted location is supposed to be further away, this targeter will instead "fall short" of it, targeting the location `maxdistance` blocks away form the original target's location, alongside its movement vector                                      | 64      |
| ticksPredicted | ticks, t | How "far into the future" this targeter should predict.          | 20      |
| ignoreTransparent | it | Whether the raytrace used for the prediction should ignore transparent blocks | true |



## Examples
```yaml
  Skills:
  - skill{s=TheFloorIsLava} @targetPredictedLoc{ticks=15}
```


## Aliases
- [x] targetPredictedLoc
- [x] TPL
- [x] PredictedTargetLocation
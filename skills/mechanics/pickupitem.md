## Description
Pick up the targeted item, if the caster is a player.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| fakelooting | fl      | Whether a fake looting animation should be played                    | true    |
| onpickup  | pickup, then | The [metaskill] to execute once the item is picked up             |<!--type:Metaskill-->|

### OnPickup Attribute
The called metaskill will have some of its linked data overriden/set to be the following
| Data     | Value  |
| -------- | ------ |
| Location | The position of the picked up item |
| Origin   | The position of the picked up item |
| Item     | The picked up item                 |


## Examples
```yaml
  Skills:
  - pickupitem @ItemsInRadius{r=10}
```


<!--TAGS-->
<!--tag:Item-->
<!--tag:World-->
<!--tag:Meta-Mechanic-->

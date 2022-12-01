Goal: Move To Block
--------------

Makes the mob move towards the specified block. 

### Attributes

| Attribute      | Aliases  | Description                                   | Default |
|----------------|----------|-----------------------------------------------|:-------:|
| material       |          | The block type to target                      |         |
| radius         |          | the radius in which to search for the block   |         |
| radiusy        |          | the y radius in which to search for the block |         |
| speed          |          | the speed of movement                         |         |


### Examples

```yaml
ExampleMob:
  Type: Pig
  AIGoalSelectors:
    - clear
    - moveToBlock{material=STONE;radius=8;radiusY=2;speed=0.9}
```
Goal: Move To Block
--------------

Makes the mob move towards the specified block type. 

### Attributes

| Attribute      | Aliases  | Description                                   | Default |
|----------------|----------|-----------------------------------------------|:-------:|
| material       |          | The block type to target                      |         |
| radius         |          | The radius in which to search for the block   |         |
| radiusy        |          | The y radius in which to search for the block |         |
| speed          |          | The speed of movement                         |         |


### Examples

```yaml
ExampleMob:
  Type: Pig
  AIGoalSelectors:
    - clear
    - moveToBlock{material=STONE;radius=8;radiusY=2;speed=0.9}
```
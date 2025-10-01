## Description

Changes the weather in the casting mob's world.

## Attributes

| Attribute | Aliases   | Description                                               | Default |
|-----------|-----------|-----------------------------------------------------------|---------|
| type      | t         | The type of weather. Can be "sunny", "rainy", or "stormy" | sunny<!--type:SUNNY,RAINY,STORMY-->|
| duration  | d         | How long (in ticks) the weather will be forced to last    | 500     |

#### Weather Types

|  Type      | Aliases          |
|------------|------------------|
| **Sunny**  | sun, clear       |
| **Rainy**  | rain             |
| **Stormy** | storm, thunder   |


## Examples:

Causes a storm for 10 minutes when the mob spawns.
```yaml
Skills:
  - weather{type=storm;duration=6000} ~onSpawn
```


<!--TAGS-->
<!--tag:World-->

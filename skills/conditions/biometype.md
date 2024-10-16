## Description
Tests if the target is within the given list of biome types



## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | t         | A list of biomes to check                                            | ocean   |
| exact     | e         | Whether to match the type exactly                                    | true    |


## Examples
```yaml
Conditions:
- biometype{t=jungle,ocean,extreme_hills} true
```

## Biome Types
- none
- taiga
- extreme_hills
- jungle
- mesa
- plains
- savanna
- icy
- the_end
- beach
- forest
- ocean
- desert
- river
- swamp
- mushroom
- nether
- underground
- mountain

## Aliases
- [x] biomecategory
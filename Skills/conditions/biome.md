## Description
This condition tests if the target is within the given list of biomes.  
If no namespace is provided, it will default to `minecraft:`

## Attributes

| Attribute | Aliases | Description               | Default          |
| --------- | --------| --------------------------|------------------|
| biome     | b       | A list of biomes to check | minecraft:plains |
| exact     | e       | Whether to match the biome exactly | true    |


## Examples

```yaml
Conditions:
- biome{b=minecraft:plains,river} true
```

If using a custom biome (like from a datapack), you can define it with the namespaced key like this:

```yaml
Conditions:
- biome{b=far_end:void,far_end:warped_marsh} true
```
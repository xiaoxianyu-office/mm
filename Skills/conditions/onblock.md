## Description
Matches the block the target entity is standing on.  
A list of available materials can be found on the [Spigot Javadoc].(https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) 


## Attributes

| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| material  | m, type, block, b | A list of materials. The condition will match if one is found| STONE   |


## Examples
```yaml
  TargetConditions:
  - onblock{m=BEDROCK,OAK_LEAVES,ACACIA_FENCE} false
```

```yaml
  TargetConditions:
  - onblock{m=DIRT,STONE,GRAVEL} true
```
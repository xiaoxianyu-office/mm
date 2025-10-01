## Description
Will break a block at the target location. This mechanic will also drop
the block (with exception of Bedrock). REQUIRES `forcesync=true`.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| doDrops   | drops, d  | Whether or not to drop the block/s                                   | true    |
| doEffect  | effect, e | Whether or not to play the break block particles                     | true    |
| useTool   | tool, t   | Whether or not to use the tool in the players hands                  | true    |


## Examples
This example would break the block at location x:100,y:64,z:100 in the
current world when right-clicked.
```yaml
Skills:
  - breakblock{forcesync=true} @location{c=100,64,100} ~onInteract
```
##
### Tests
> These tests were run using /mm test cast TestingBreakBlock
 
```yaml
TestingBreakBlock:
  Skills:
  - breakblock{forcesync=true;doEffect=true;doDrops=true;useTool=true} @origin
```

When a player calls this without a tool in there hand it does not drop a block or create the particle effects.
## 
```yaml
TestingBreakBlock:
  Skills:
  - breakblock{forcesync=true;doEffect=true;doDrops=true;useTool=false} @origin
```

When a player calls this without a tool in there hand it does drop the block, but does not create the particle effects. The same is true if setting doEffect to false. 

##
```yaml
TestingBreakBlock:
  Skills:
  - breakblock{forcesync=true;doEffect=false;doDrops=true;useTool=true} @origin
```

When a player calls this with a tool in their hand it drops the block and does not play the particle effects. 

##
```yaml
TestingBreakBlock:
  Skills:
  - breakblock{forcesync=true;doEffect=true;doDrops=false;useTool=true} @origin
```

When a player calls this with a tool in their hand it does not drop a block, nor does it create the particle effects.

##
```yaml
TestingBreakBlock:
  Skills:
  - breakblock{forcesync=true;doEffect=true;doDrops=true;useTool=true} @origin
```

When a player calls this with a tool in their hand it does drop a block, and does create the particle effects.


## Aliases
- [x] blockBreak


<!--TAGS-->
<!--tag:World-->
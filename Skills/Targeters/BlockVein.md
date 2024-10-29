## Description
Target all adjancent blocks that match the blocktype, starting from the origin of the skill


## Attributes
| Attribute      | Aliases         | Description                                            | Default |
|----------------|-----------------|--------------------------------------------------------|---------|
| blocktypes     | blocktype, bt, t, material, materials, mat, m, blocks, block, b                        | Blocks to add to the vein. Can be a list.<br>You can add a `*` at the front of the type to indicate that the one specified is not a block type, but a [block tag](https://minecraft.wiki/w/Tag#Block_tags_2) (example: `blocktype=*sculk_replaceable` )| STONE   |
| limit          | max, l, m       | Limit of the number of blocks added to the vein.       | 10      |
| originMustMatch| match           | Should the targeted blocks match the one at the origin of the metaskill                                                                                   | true    |


## Examples
```yaml
# Vein mine whatever you mine (Crucible)
VeinMinerPickaxe:
  Id: NETHERITE_PICKAXE
  Skills:
  - breakblock{origin=@TargetBlock} @Vein{bt=<caster.raycast>} ~onBlockBreak

# Vein mine only certain ores (Crucible)
VeinMinerPickaxeOres:
  Id: DIAMOND_PICKAXE
  Skills:
  - breakblock{origin=@TargetBlock} @Vein{bt=REDSTONE_ORE, DEEPSLATE_REDSTONE_ORE} ~onBlockBreak

# Vein mine all ores (Crucible)
VeinMinerPickaxeOres_V2:
  Id: DIAMOND_PICKAXE
  Skills:
  - breakblock{origin=@TargetBlock} @Vein{bt=#_ORE} ~onBlockBreak
```


## Aliases
- [x] vein
- [x] bv
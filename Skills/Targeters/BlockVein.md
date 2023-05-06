## Targeter: BlockVein
Target all adjancent blocks that match the blocktype, starting from the origin of the skill

### Attributes

| Attribute      | Aliases         | Description                                            | Default |
|----------------|-----------------|--------------------------------------------------------|:-------:|
| blocktypes     | blocktype, bt, t, material, materials, mat, m, blocks, block, b                        | Blocks to add to the vein. Can be a list.                                                 | STONE   |
| limit          | max, l, m       | Limit of the number of blocks added to the vein.       | 10      |
| originMustMatch| match           | Should the targeted blocks match the one at the origin of the metaskill                                                                                   | true    |

## Examples
```yaml
# Vein mine whatever you mine
VeinMinerPickaxe:
  Id: NETHERITE_PICKAXE
  Skills:
  - breakblock{origin=@TargetBlock} @Vein{bt=<caster.raycast>} ~onBlockBreak

# Vein mine only certain ores
VeinMinerPickaxeOres:
  Id: DIAMOND_PICKAXE
  Skills:
  - breakblock{origin=@TargetBlock} @Vein{bt=REDSTONE_ORE, DEEPSLATE_REDSTONE_ORE} ~onBlockBreak

# Vein mine all ores
VeinMinerPickaxeOres_V2:
  Id: DIAMOND_PICKAXE
  Skills:
  - breakblock{origin=@TargetBlock} @Vein{bt=#_ORE} ~onBlockBreak
```
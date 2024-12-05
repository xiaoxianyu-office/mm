## Description 
Drops a [Mythic Item](/Items/Items)


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| level     | lvl, l    | The level of the item                                                |         |
| lootsplosion | lootsplosionenabled, ls | Whether lootsplosion should be enabled              |         |
| itemvfx   | itemvfxenabled, iv | Whether item vfx should be enabled                          |         |
| itemvfxmaterial | itemvfxmaterial, ivm | The material of the item vfx                        |         |
| vfxdata   | vfxd      | The custom model data of the material for the item vfx               |         |
| vfxcolor  | vfxc, color | The color of the item vfx                                          |         |
| hologramname | hologramnameenabled, hn | Whether an hologram for the drop should be enabled  |         |
| clientsidedrops | clientsidedropsenabled, csd | Whether client side drops should be enabled  |         |
| itemglowcolor | glowcolor, gc | The glow color of the drop                                   |         |
| itembeamcolor | beamColor, bc | The beam color of the drop                                   |         |
| billboarding | billboard, bill | Billboarding for the drop                                   |         |
| brightness | bright, b | Brightness of the drop                                              |         |


## Examples
```yaml
  Drops:
  - SuperCoolItem{lootsplosion=true} 2 0.5
```
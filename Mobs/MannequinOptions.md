All available mannequin entity options. All of these options go under the `MannequinOptions` sections, like so:
```yml
cool_display:
  Type: MANNEQUIN
  MannequinOptions:
    Player: Herobrine
```

_[TOC]_

#### Immovable
Whether the mannequin should be immovable  
Defaults to `false`
```yaml
  MannequinOptions:
    Immovable: true
```

#### Description
The mannequin's description. Will appear below the mannequin's name.      
```yaml
  MannequinOptions:
    Description: "Hello World!"
```

#### HideDescription
Whether the hide the mannequin's description    
Defaults to `false`
```yaml
  MannequinOptions:
    HideDescription: true
```

#### MainHand
Which hand should be the main one.    
Can be either LEFT or RIGHT (The possible values of this [MainHand Spigot Enum](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/inventory/MainHand.html))
```yaml
  MannequinOptions:
    MainHand: LEFT
```

#### Pose
The pose of the mannequin.  
Can be any of the poses available in the [Pose Spigot Enum](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/entity/Pose.html)
```yaml
  MannequinOptions:
    Pose: DYING
```

#### Player
The player whose skin to use for the mannequin's  
Defaults to `Ashijin`
```yaml
  MannequinOptions:
    Player: _xXSuperN00B67Xx_
```

#### Skin
The texture to use for the mannequin's skin  
Reference the [minecraft wiki](https://minecraft.wiki/w/Mannequin#Entity_data:~:text=%5BString%5D%C2%A0texture,a%20default%20skin.) to know more
```yaml
  MannequinOptions:
    Skin: namespace:directory/texturename
```

#### Cape
The texture to use for the mannequin's cape    
Reference the [minecraft wiki](https://minecraft.wiki/w/Mannequin#Entity_data:~:text=%5BString%5D%C2%A0cape,displaying%20no%20cape.) to know more
```yaml
  MannequinOptions:
    Cape: namespace:directory/texturename
```

#### Elytra
The texture to use for the mannequin's elytra
Reference the [minecraft wiki](https://minecraft.wiki/w/Mannequin#Entity_data:~:text=%5BString%5D%C2%A0elytra,the%20default%20elytra.) to know more
```yaml
  MannequinOptions:
    Elytra: namespace:directory/texturename
```

#### Model
The model type of the mannequin.  
Can be any of the models available in the [SkinModel Spigot Enum](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/profile/PlayerTextures.SkinModel.html)  
Defaults to `CLASSIC`
```yaml
  MannequinOptions:
    Model: SLIM
```
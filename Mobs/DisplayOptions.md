All available display entity options. All of these options go under the `DisplayOptions` sections, like so:
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
```
Table Of Contents:

[[_TOC_]]

# Base Options
These options are available for all display entity types.

#### ViewRange
The maximum view range/distance. [When the distance is more than `viewRange x entityDistanceScaling x 64`, the entity is not rendered](https://minecraft.wiki/w/Display#Entity_data). Defaults to `1`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    ViewRange: 1
```

#### Width
The display width. Defaults to `0`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    Width: 0
```

#### Height
The display height. Defaults to `0`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    Height: 0
```

#### ShadowRadius
The display's shadow radius. Defaults to `0`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    ShadowRadius: 0
```

#### ShadowStrength
The opacity of the display entity's shadow. Defaults to `1`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    ShadowStrength: 1
```

#### Billboard
Controls where the display entity pivots when rendered to the player. Defaults to `FIXED`.\
Available constraints:

| Billboard  | Description                       |
|------------|-----------------------------------|
| FIXED      | No rotation                       |
| CENTER     | Pivots around the center point    |
| HORIZONTAL | Pivots around the horizontal axis |
| VERTICAL   | Pivots around the vertical axis   |

```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    Billboard: FIXED
```

#### TeleportDuration
Set the teleport duration in ticks. Defaults to `0`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    TeleportDuration: 0
```
#### InterpolationDelay
Set the delay before starting interpolation. Defaults to `0`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    InterpolationDelay: 0
```

#### InterpolationDuration
Set the interpolation duration in ticks. Defaults to `0`.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    InterpolationDuration: 0
```

#### ColorOverride
Set the glow border color. If `0`, it uses the color of the team the display team is in. Defaults to `0`.\
**Formats**: `a,r,g,b` or an integer equivalent. 
Here are sites that you can use: [color-hex](https://www.color-hex.com/), [arg-int-calculator](https://argb-int-calculator.netlify.app/) 
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    ColorOverride: 0
```

### Brightness
Both blocklight and skylight must be set to override brightness. Values must be in range of `0` to `15`. 
 
Use a value of `-1` to make it so the display entity uses the ambiens's blocklight/skylight without overriding them

#### BlockLight & SkyLight
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    BlockLight: 0
    SkyLight: 0
```

### Transformations
#### Translation
Set the display entity translation. Defaults to `0,0,0`.
**Format**: x,y,z
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    Translation: 0,0,0
```

#### Scale
Set the scale of the display entity. Scales the model centered on the origin. Defaults to `1,1,1`.
**Format**: x,y,z
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    Scale: 1,1,1
```

#### LeftRotation
Set the left rotation using [quaternions](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation) if 4 values are provided (x,y,z,w).  
Uses euler if 3 are provided (x,y,z).  
Defaults to `0,0,0,1` (no rotation).  
**Format**: x,y,z,w
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    LeftRotation: 0,0,0,1
```

#### RightRotation
Set the left rotation using [quaternions](https://en.wikipedia.org/wiki/Quaternions_and_spatial_rotation) if 4 values are provided (x,y,z,w).  
Uses eular if 3 are provided (x,y,z).  
Defaults to `0,0,0,1` (no rotation).  
**Format**: x,y,z,w
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: grass_block
    RightRotation: 0,0,0,1
```

# Block Display
This display type only has one special option.
#### Block
The block state to use.
```yml
cool_display:
  Type: block_display
  DisplayOptions:
    Block: bell[facing=north]
```

# Item Display

#### Item
The item to use. Supports mythic items.
```yml
cool_display:
  Type: item_display
  DisplayOptions:
    Item: stick
```

#### Transform
The model transform applied to the item. Defaults to `NONE`.

|          Types          |
|:-----------------------:|
|  FIRSTPERSON_LEFTHAND   |
|  FIRSTPERSON_RIGHTHAND  |
|          FIXED          |
|         GROUND          |
|           GUI           |
|          HEAD           |
|          NONE           |
|  THIRDPERSON_LEFTHAND   |
|  THIRDPERSON_RIGHTHAND  |

```yml
cool_display:
  Type: item_display
  DisplayOptions:
    Item: stick
    Transform: NONE
```

# Text Display
#### Text
Set the text to show. Defaults to `Give This Poor Dude A Text To Display`.
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
```

#### Opacity
Set the text opacity, ranging from `0` to `255`. Defaults to `255`.
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    Opacity: 255
```

#### DefaultBackground
Set whether to render using the default text background color (same as in chat),
overriding the [BackgroundColor](#BackgroundColor) option.
Defaults to `false`.
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    DefaultBackground: false
```

#### BackgroundColor
Set the text background color.
Defaults to `1073741824`.\
**Formats**: `a,r,g,b` or an integer equivalent.
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    BackgroundColor: 1073741824
```

#### Alignment
Set the text alignment. Defaults to `CENTER`.

| Types  | Description         |
|:------:|---------------------|
| CENTER | Center aligned text |
|  LEFT  | Left aligned text   |
| RIGHT  | Right aligned text  |

```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    Alignment: CENTER
```

#### LineWidth
The maximum line width used to split lines. Can also use `\n` characters to split to another line. Defaults to `200`.
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    LineWidth: 200
```

#### Shadowed
Set whether the text should be displayed with a shadow. Defaults to `false`.
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    Shadowed: false
```

#### SeeThrough
Set whether the text should be visible through blocks. Defaults to `false`
```yml
cool_display:
  Type: text_display
  DisplayOptions:
    Text: Give This Poor Dude A Text To Display
    SeeThrough: false
```
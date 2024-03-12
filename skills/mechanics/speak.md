## Description
Makes the caster speak using chat and speech bubbles. Supports
Holograms.

* Now allow hex colors in the format **`<#FFFFFF>`**
* Now supports gradients in the format **`<gradient:#color1:#color2>text</gradient>`**
* Now supports **`<rainbow>text</rainbow>`**
* Now supports hover text in the format **`<hover:show_text:'hover text??'>hover over me!</hover>`**
* Now supports clickable text in the format **`<click:run_command:/say hello>click me!</click>`**
* You can force a new line in the hologram by using `\n`

## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| offset    | o         | The y offset for the hologram.                                       | 0.6     |
| radius    | r         | The radius of entities which will see the chat message               | 12      |
| maxlinelength | ll, mll, ml | The maximum length of the hologram                             | 22      |
| lineprefix| lp        | The prefix for the hologram.                                         | &f      |
| message   | m         | The message to be displayed (affects both hologram and chat)         |         |
| chatprefix| cp       | The prefix for the chat message                                       | &lt;caster.name&gt;&f&lt;&co&gt;  |
| duration  | d, t      | The amount of time the hologram will be displayed for.               | MESSAGE LENGTH * 4  |
| sendchatmessage | chatmessage, chat | Whether the message shows up in chat                   | true    |
| audience  |           | The [Audience] of the mechanic                                       | tracked |
  

## Examples
```yaml
  Skills:
  - speak{
    offset=0.6f;
    radius=30;
    maxlinelength=22;
    lineprefix="&5";
    message=" I just spawned!";
    chatprefix=<caster.name>&f<&co>;
    duration=200} @self ~onSpawn
```


<!-- LINKS -->
[audience]: Skills/Audience
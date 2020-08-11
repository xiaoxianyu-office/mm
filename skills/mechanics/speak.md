Mechanic: Speak
===============

Makes the caster speak using chat and speech bubbles. Supports
Holograms.

Attributes
----------

| Attribute     | Aliases     | Description                                                   | Default Value                    |
|---------------|-------------|---------------------------------------------------------------|----------------------------------|
| offset        | o           | The y offset for the hologram.                                | 0.6f                             |
| radius        | r           | The radius of entities which will see the chat message .      | 12                               |
| maxlinelength | ll, mll, ml | The maximum length of the hologram.                           | 22                               |
| lineprefix    | lp          | The prefix for the hologram.                                  | &f                               |
| message       | m           | The message to be displayed (affects both hologram and chat). | NONE                             |
| chatprefix    | cp          | The prefix for the chat message.                              | &lt;caster.name&gt;&f&lt;&co&gt; |
| duration      | d, t        | The amount of time the hologram will be displayed for.        | MESSAGE LENGTH * 4              |

  

Examples
--------

      Skills:
      - speak{offset=0.6f;radius=30;maxlinelength=22;lineprefix="&5";message=" I just spawned!";chatprefix=<caster.name>&f<&co>;duration=200} @self ~onSpawn
      - ...

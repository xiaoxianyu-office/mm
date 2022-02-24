Mechanic: Glow
==============

Makes the target entity glow (using the Glowing potion effect.)

Can have a color specified.

**REQUIRES THE PLUGIN [GLOW
API](https://www.spigotmc.org/resources/api-glowapi-1-9-1-10.19422/)**

Attributes
----------

| Attribute | Aliases | Description                     | Default |
|-----------|---------|---------------------------------|---------|
| color     | c       | The color the entity will glow: BLACK, DARK_BLUE, DARK_GREEN, DARK_AQUA, DARK_RED, DARK_PURPLE, GOLD, GRAY, DARK_GRAY, BLUE, GREEN, AQUA, RED, PURPLE, YELLOW, or WHITE | white   |
| duration  | d       | How long the effect will last.  | 100     |

Examples
--------

      Skills:
      - effect:glow{color=RED;duration=1000}

Makes the target glow red for 1000 ticks (50 seconds).
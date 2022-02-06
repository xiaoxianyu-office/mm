Mechanic: GoTo
============================

Tells a mob to GoTo a location or an entity targeter

Attributes
----------

| Attribute   | Aliases | Description                        | Default Value |
|-------------|---------|------------------------------------|---------------|
| maxDistance | md      | max distance it should travel                                                     | 64          |
| spreadH     | sh      | Amount of horizontal spread it can be away from the target its moving towards                                  | 0           |
| spreadV     | sv      | Amount of vertical spread it can be away from the target its moving towards                                 | 0          |

  

Examples
--------

    Skills:
    - goto{maxDistance=64;sh=5;sv=5} @owner
    - goto{maxDistance=32;sh=5;sv=5} @location{c=100,65,100}
    - ...
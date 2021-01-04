Mechanic: Disguise
==================

Runs a disguise string on the casting mob. This skill requires Libs'
Disguises and ProtocolLib be installed to enable Disguise functionality.

See [Add-On: Disguises](/addons/disguises/start) for a list of available
disguises.

Attributes
----------

Any [disguise-specific
options](http://mythicmobs.net/manual/doku.php/addons/disguises/start#options)
can also be used as an attribute in the skill.

| Attribute | Aliases | Description                       | Default |
|-----------|---------|-----------------------------------|---------|
| disguise  | d, type | The disguise to apply to the mob. |         |

  

Examples
--------

This example would cause the mob to turn into a sheep.

      Skills:
      - disguise{d=SHEEP}

Configure custom disguises using Lib's Disguises for more granular detail.
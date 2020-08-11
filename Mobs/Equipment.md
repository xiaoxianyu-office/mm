The Equipment section in a mob config is a special droptable that
defines what kind of equipment the mob will spawn with. The equipment
will only be applied to the mob when it spawns or during a reload, and
can be changed afterwards by using the [Equip
mechanic](/skills/mechanics/equip).

If you want your mob to not wear any kind of equipment, you can use the
option "PreventRandomEquipment". See [Mob
Options](/databases/mobs/options). An alternative to using that option
is to equip your mob with *dummy items*. Such items need have the item
ID AIR.

Equipment is a special type of droptable and can reference other
droptables, allowing you to use drop conditions to create advanced
equipment sets. If you define the slot in a droptable and reference it
normally in the Equipment section (or equip skill), the mob will "equip"
the drops instead of dropping them.

Syntax
------

    internal_mobname:
      Type: <mobtype>
      Equipment:
      - <item> <slot>
      - <item> <slot>
      - ...

**&lt;item&gt;**  
Can be either the name of a [MythicMobs item](/databases/items/overview)
or a vanilla item.

**&lt;slot&gt;**  
Defines the slot on the mob that item should be carried on.

| Slot    | Description                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| HEAD    | The head slot. Apart from regular helmets can be any blocktype or player head. Most will render accurately. |
| CHEST   | The chest slot. Will only render chestplates, but will carry any items.                                     |
| LEGS    | The leg slot. Will only render leggings, but will carry any items.                                          |
| FEET    | The feet slot. Will only render boots, but will carry any items.                                            |
| HAND    | The mainhand slot. Will render any type of item.                                                            |
| OFFHAND | The offhand slot, introduced in MC 1.9. Will render any type of item.                                       |

Examples
--------

    awesome_boss:
      Type: pig_zombie
      Equipment:
      - awesome_boss_helmet:4
      - diamond_sword:0

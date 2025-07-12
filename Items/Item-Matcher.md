Some features inside of MythicMobs supports matching items or blocks via a specific syntax:

##

Writing the internal name of a Mythic Item/[Mythic (Crucible) Custom Block](/../../../mythiccrucible/-/wikis/Custom-Blocks) will match
  - that specific Mythic Item
  - that specific Mythic Custom Block

##

Writing the [Spigot material type](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html) will match
  - items with that material type
  - blocks with that material type

##

Using `#` at the start of an entry will match against
  - items with that [Item Tag](https://minecraft.wiki/w/Tag#Item_tags_2)
    - `#arrows`, `#axes` and so on
  - blocks with that [Block Tag](https://minecraft.wiki/w/Tag#Block_tags_2)
    - `#air`, `#animals_spawnable_on` and so on

##

Using `*` at any point in the entry will make it so any * present will match against any number of characters. For those familiar with Regex syntax, `*` is equal to `.*`
  - `netherite_*` will match any item/block whose type stars with "netherite_"
  - `*_log` will match any item/block whose type ends in "_log"
  - `*a*` will match any item/block whose type has the letter "a" somewhere in it
  - `*` will match anything

##

For blocks only, it is possible to specify some specific [block states](https://minecraft.wiki/w/Block_states) to be matched by specifying them inside of a pair of square brackets `[]` after the entry
  - redstone_torch[lit=true;facing=north]


<!-- 

| Attribute ITEMMATCHER | Aliases   | Description                                              | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| strict    | exact, e  | Whether the matcher should more strictly match the target item       | false   |
| types     | type, t, material, mat, m, item, i | The items to match. Can be a list           | DIRT    |
| vanillaonly | vanilla | Whether the matched item can only be a vanilla one                   | false   |

-->
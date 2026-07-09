## Description
Tests if the entity type of the target is the specified one.  
A list of valid entity types can be found on the [Spigot Javadocs](https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html).


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| type      | types, t  | A list of entity types to match                                      |<!--type:EntityType--><!--list--> |


## Per-Type Constraints
Each entry in the `type` list can carry a nested block that further restricts the match to entities with specific traits, using the form `type=TYPE{option=value;option=value}`.  
An entity of that type matches only if every option in its block matches, and an option matches if the entity's value equals any of the values listed for it. Values are case insensitive, and dashes and spaces are treated as underscores.  
Constraint options only apply to entities that expose the matching trait. All other entity types ignore the option and fail the constraint.

| Option | Aliases | Applies To | Description |
|--------|---------|------------|-------------|
| variant | v | Frog, Axolotl, Cat, Rabbit, Fox, Villager, Mooshroom, Cow, Chicken, Pig, Wolf, Zombie Nautilus (1.21.11+), Copper Golem (1.21.9+) | The variant to match. For a Copper Golem this is the weathering state |
| color | c | Horse, Sheep, Shulker, Parrot, Llama, Trader Llama | The color to match. A Sheep named `jeb_` matches `RAINBOW` |
| style | s | Horse | The horse markings style to match |
| mainGene | maingene, main, mg | Panda | The panda main gene to match |
| hiddenGene | hiddengene, hidden, hg | Panda | The panda hidden gene to match |
| biome | b | Villager, Zombie Villager | The villager biome type to match |
| profession | prof, proffesion | Villager, Zombie Villager | The villager profession to match |
| crack | cracks, crackedness, crackiness | Iron Golem | The crack level derived from health: `NONE`, `LOW`, `MEDIUM`, `HIGH` |
| bodyColor | bodycolor, body, bc | Tropical Fish | The body color to match |
| patternColor | patterncolor, pc | Tropical Fish | The pattern color to match |
| pattern | p | Tropical Fish | The tropical fish pattern to match |

```yaml
TargetConditions:
- entityType{type=HORSE{color=WHITE;style=WHITE_DOTS}} true
```

```yaml
TargetConditions:
- entityType{type=CAT{variant=TABBY}} true
```

```yaml
TargetConditions:
- entityType{type=TROPICAL_FISH{bodyColor=WHITE;patternColor=RED;pattern=FLOPPER}} true
```


## Examples
```yaml
Conditions:
- entitytype{t=ZOMBIE} true
```

```yaml
TargetConditions:
- entitytype{t=WITCH} true
```

```yaml
TriggerConditions:
- entitytype{t=PLAYER} true
```

## Aliases
- [x] mobtype
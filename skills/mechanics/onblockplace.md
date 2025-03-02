## Description
Applies an aura to the target that triggers a skill when they place a block


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| onPlaceSkill | onplace, op | Skill to execute if the target places a block                   |<!--type:Metaskill-->|
| cancelEvent  | cancel, cE  | Whether or not to cancel the event that triggered the aura      | false   |

> This mechanic inherits every attribute of the [aura] mechanic


## Examples
Simple:

Apply an onBlockPlace aura on yourself. Whenever you place a block, it will change the terrain around it into gold blocks (Midas Touch). Here we use 2 meta-skills in order to make the @BlocksInRadius be centered around the @targetlocation, which is where the block will is placed. If you don't use 2 meta-skills the @BlocksInRadius will be centered around the person who placed the block instead. 
```yaml
ApplyAura:
  Skills:
  - onBlockPlace{op=MidasTouch1;auraname=Golden;d=300;i=1} @self
MidasTouch1:
  Skills:
  - skill{s=MidasTouch2} @targetlocation
MidasTouch2:
  Skills:
  - setblock{m=GOLD_BLOCK} @BlocksInRadius{r=5;ry=1}
```

##

Intermediate:

Apply an onBlockPlace aura on yourself. When you place a block make it turn all non valueable ore blocks into glass. This is effectively an X-Ray ability. We have 2 meta-skills again this time, but we are not focusing the skill around the block place location. We use the second meta-skill to make sure that we do not set any valuable ore blocks to glass instead. We could center it around the block place location, you would just use 3 meta-skills instead, merging the top example with this one.

If you don't want this xray to be permanent you can try using blockmask with material set to glass instead of using the setblock mechanic. Blockmask uses packets, so can cause client lag. Play around with it! its the best way to learn. 
```yaml
ApplyAura:
  Skills:
  - onBlockPlace{op=XRay;auraname=Cheater;d=200;i=1} @self
XRay:
  Skills:
  - skill{s=XRay2} @BlocksInRadius{r=20;ry=20}
XRay2:
  TargetConditions:
  - blocktype{type=BEDROCK,END_PORTAL,END_PORTAL_FRAME,NETHER_PORTAL,CRAFTING_TABLE,SMITHING_TABLE,ENCHANTING_TABLE,COAL_ORE,DEEPSLATE_COAL_ORE,DIAMOND_ORE,DEEPSLATE_DIAMOND_ORE,EMERALD_ORE,DEEPSLATE_EMERALD_ORE,GOLD_ORE,NETHER_GOLD_ORE,DEEPSLATE_GOLD_ORE,NETHER_QUARTZ_ORE,IRON_ORE,DEEPSLATE_IRON_ORE,COPPER_ORE,DEEPSLATE_COPPER_ORE,LAPIS_ORE,DEEPSLATE_LAPIS_ORE,REDSTONE_ORE,DEEPSLATE_REDSTONE_ORE,ANCIENT_DEBRIS} false
  Skills:
  - setblock{m=GLASS}
```


## Aliases
- [x] onplaceblock


<!-- LINKS -->
[aura]: /skills/mechanics/aura


<!--TAGS-->
<!--tag:Meta-Mechanic:Aura-->
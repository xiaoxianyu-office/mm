Mechanic: onBlockBreak
==================

Applies an aura to the target that triggers a skill when they break a block

Attributes
----------

| Attribute        | Aliases       | Description                                                | Default Value |
|------------------|---------------|------------------------------------------------------------|---------------|
| onBlockBreak     | oB            | Skill to execute if the target hits something              | NONE |
| cancelEvent      | cE            | Whether or not to cancel the event that triggered the aura | false         |

  

Examples
--------

Simple:

Apply an onBlockBreak aura to yourself that makes particles happen at the location of the broken block

    ApplyAura:
      Skills:
      - onBlockBreak{oB=FlameParticlesAtBlock;cE=false;auraname=Fire;d=300;i=1} @self
    FlameParticlesAtBlock:
      Skills:
      - particles{particle=flame;a=2;hs=0.25;vs=0.25;y=0.5;s=0.1125} @targetlocation

Intermediate: (because you can crash / lag you server if you don't read this!)

Apply an onBlockBreak aura to yourself, then when you break blocks it'll mine in a 5x5 area (3 radius in each direction from center block) based on the targetlocation of the block you broke. The cooldown here is REQUIRED. Without the cooldown the breakblock mechanic will retrigger the onblockbreak aura infinitely. You need MINIMUM cooldown of 0.1 seconds (2 ticks). 

We need the 2 meta-skills here so that we can force the blockinradius to work at the block you broke. Without using 2 meta-skills, the blocksInRadius will target the blocks around the player who broke the blocks instead of the location the blocks were broken.


    ApplyAura:
      Skills:
      - onBlockBreak{oB=AreaMining1;cE=false;auraname=TotalDestruction;d=300;i=1} @self
    AreaMining1:
      Cooldown: 0.1
      Skills:
      - skill{s=AreaMining2} @targetLocation
    AreaMining2:
      Skills:
      - breakblock{doDrops=true;doEffect=true;useTool=false;forcesync=true} @BlocksInRadius{r=3;ry=3}
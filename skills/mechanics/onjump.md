Mechanic: onJump
==================

PAPER ONLY MECHANIC

Applies an aura to the target that triggers a skill when they jump

Attributes
----------

| Attribute        | Aliases       | Description                                                | Default Value |
|------------------|---------------|------------------------------------------------------------|---------------|
| onJump     | oj            | Skill to execute if the target jumps            | NONE |
| cancelevent | cE           | cancel the event when it is triggered           | false |


Examples
--------

Simple 1: 

Apply an onJump aura to yourself. Whenever you jump it will put level 1 slow falling on you for 1 second.

    ApplyAura:
      Skills:
      - onJump{oj=SlowFalling;auraname=Jumpies;d=300;i=1} @self

    SlowFalling:
      Skills:
      - potion{t=SLOW_FALLING;d=20;l=0;hasParticles=false} @self

Simple 2:

Apply an onJump aura to yourself. Whenever you jump teleport to the closest entity within 40 blocks and kill them.

    ApplyAura:
      Skills:
      - onJump{oj=Assassin;auraname=Stabbies;d=300;i=1} @self

    Assassin:
      Skills:
      - skill{s=Murder} @EIR{r=30;limit=1;sort=NEAREST;targetPlayers=false}

    Murder:
      Skills:
      - teleport
      - delay 1
      - damage{a=1000-2000;cause=thorns}

Intermediate:

Apply an onJump aura to yourself. Whenever you jump, jump higher into the air, then stop mid air and shoot projectiles at every entities within 30 blocks of you repeatedly. 

    ApplyAura:
      Skills:
      - onJump{oj=PewPew;auraname=Shooties;d=300;i=1} @self
    PewPew:
      Skills:
      - jump{v=2;delay=2} @self
      - delay 10
      - velocity{m=SET;x=0;y=0;z=0;repeat=39;repeatInterval=1} @self
      - skill{s=ShotEm;repeat=19;repeatInterval=2} @EIR{r=30;limit=10;sort=RANDOM;targetPlayers=false}
    ShotEm:
      Skills:  
      - projectile{bulletType=ITEM;material=FIRE_CHARGE;bulletSpin=29;i=1;v=24;mr=100;d=100;hnp=true;oS=Fireball_oS;oT=Fireball_oT;oH=Fireball_oH}
    Fireball_oS:
      Skills:
      - sound{s=entity.skeleton.shoot;v=1;p=1} @origin
    Fireball_oT:
      Skills:
      - particles{particle=flame;a=4;hs=0.2;vs=0.2;y=0;s=0.1} @origin
    Fireball_oH:
      Skills:
      - damage{a=5-15;cause=magic}
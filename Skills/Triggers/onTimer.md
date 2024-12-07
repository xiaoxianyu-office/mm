## Description
This Trigger has a special syntax: `~onTimer:<ticks>`  

Executes the skill every *n<sup>th</sup>* ticks. Ticks can't be zero and 20 ticks is equal to 1 second.  

This trigger does not act relatively to the mob's spawn time, but to a global clock. So, for instance, if you have `~onTimer:1000`, its first execution could be in any moment between mob spawn and 1000 ticks from it depending on the value of the global clock.

> Care must be taken when using this trigger as it can lead to server/client performance issues!
>i.e. large amounts of particle effects can cause client lag, or can kick the client from the server

> There is no associated [@trigger](/Skills/Targeters/Trigger).


## Implementations
- [MythicCrucible](/../../../mythiccrucible/-/wikis/Skills/Triggers/onTimer)


## Examples
```yml
EXAMPLE_MOB:
  Type: CHICKEN
  Skills:
    # sends a message to all the players in the world every 0.05 seconds
    - message{m=TIMER every tick (0.05 seconds)} @World ~onTimer:1
    # sends a message to all the players in the world every 2 seconds
    - message{m=TIMER every 40 ticks (2 seconds)} @World ~onTimer:40
```
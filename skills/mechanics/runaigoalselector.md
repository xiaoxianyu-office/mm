Mechanic: RunAIGoalSelector
===========================

**Aliases**: aigoal

Change pathfindergoals. It is not possible to use every goal on every
entity. To change the ai of an entity, you need to use clear first.
After that you can use the runaigoalselector and add the goals you need.
Unlike the mob configuration, if you use the runaigoalselector skill,
you can only use one pathfindergoal in the mechanic. But aslong as you
dont use clear, the pathfindergoal is added to the end of the already
existing goals of the entity.

A list of AI Goals can be found
[here](/Mobs/Custom-AI#ai-goal-selectors)

Example
-------

Skill.yml:

    ChangePatchfinderGoalExample:
      Skills:
      - runaigoalselector{goal=clear}
      - runaigoalselector{goal=fleesun}
      - runaigoalselector{goal=randomstroll}
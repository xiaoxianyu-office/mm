Mechanic: RunAITargetSelector
=============================

**Aliases**: aitarget

Change target pathfindergoals. It is not possible to use every goal on
every entity. To change the ai of an entity, you need to use clear
first. After that you can use the runaitargetselector and add the goals
you need. Unlike the mob configuration, if you use the
runaitargetselector skill, you can only use one pathfindergoal in the
mechanic. But aslong as you dont use clear, the pathfindergoal is added
to the end of the already existing goals of the entity.

A list of available targets can be found [here](/Mobs/Custom-AI#ai-target-selectors)

Example
-------

Skill.yml:

    ChangePatchfinderGoalExample:
      Skills:
      - runaitargetselector{target=clear}
      - runaitargetselector{target=players}
      - runaitargetselector{target=monsters}
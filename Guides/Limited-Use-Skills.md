**Difficulty: Intermediate**

There may be times when you want your skills to only be used a certain ammount of times, maybe you have a Zombie that can shoot 7 fireballs, in this guide we'll be doing just that!

We will be using variables to keep track of how many times a skill has been used, and once it reaches the total amount we want to use, the skill will stop working. 

To keep things neat and compact we will be using [in-line conditions](/Skills/conditions/in-linetargetconditions), so if you don't know about those, go read up on them!

# Specific Uses
This example will add to a variable, but once it reaches 7 the skill will stop working.
```yaml
FireballSkill:
  Conditions:
  - variableequals{var=caster.fireballs;val="7"} false
  Skills:
  - setvariable{var=caster.fireballs;val="0"} ?!variableisset{var=caster.fireballs}
  - <Your skills mechanics go here>
  - variableadd{var=caster.fireballs;a=1}
```
In this example, we are setting the variable when the skill first runs, and using an in-line condition to make sure the variable isn't already set, then we run our skills mechanics as we normally would, and once we get to the end of the skill, we increase the variable by 1.

Our skill has the [VariableEquals](/skills/conditions/variableequals) condition set which means that once the variable reaches 7, the condition will prevent the skill from running.

If you would like to reset the counter you can simply using the [VariableUnset]() mechanic.
```yaml
Skills:
- variableunset{var=caster.fireballs}
```
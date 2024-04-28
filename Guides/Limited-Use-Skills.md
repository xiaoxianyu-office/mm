**Difficulty: Intermediate**

There may be times when you want your skills to only be used a certain ammount of times, maybe you have a Zombie that can shoot 7 fireballs, in this guide we'll be doing just that!

We will be using variables to keep track of how many times a skill has been used, and once it reaches the total amount we want to use, the skill will stop working. 

# Specific Uses
This example will add to a variable, but once it reaches 7 the skill will stop working.
```yaml
FireballSkill:
  Conditions:
  - variableequals{var=caster.fireballs;val=7} false
  Skills:
  - setvariable{var=caster.fireballs;val=<caster.var.fireballs|0>+1}
  - <Your skills mechanics go here>
```
In this example, we are adding a value of "1" to the variable each time the skill is run, setting it to 1 if the variable does not exist at all via [variable fallbacks](/Skills/Variables#variable-fallback), then we run our mechanics as we normally would.

Our skill has the [VariableEquals](/skills/conditions/variableequals) condition set which means that once the variable reaches 7, the condition will prevent the skill from running.

If you would like to reset the counter you can simply using the [VariableUnset]() mechanic.
```yaml
Skills:
- variableunset{var=caster.fireballs}
```
<!--
To the other wiki editors: don't touch my child.
- Lxlp
-->

Normally, to execute a mechanic or a metaskill, you need to have that mechanic or metaskill written physically down in the config.
But with Dynamic Metaskills this you are now able to:
- execute single mechanics or entire metaskills even if they never existed before by dynamically constructing them.
- bypass missing placeholder support in mechanics/inline conditions
- store entire metaskills into variables or NBTs, enabling you to dynamically call them later

# DISCLAIMER
This is not an intended mechanic. It's just a happy accident that, somehow, consistently works. Do not expect this to be cutting edge, as, again, this is more of a convenient bug.

Since this is pretty much uncharted territory, if you have any information useful to further expand this page and, by proxy, the knowledge available to every other MythicMobs user, let me know: [Lxlp's Discord Profile](https://discord.com/users/353257382811533322)

## How does this works?
Basically, it all boils down to two things:
- The usage of the [variableskill mechanic](/skills/mechanics/variableskill)
- The existence of [inline metaskills]: /Skills/Metaskills#inline-metaskills

By combining those two things, it is now possible to do something like this
```yaml
Testmob:
  Type: pig
  Skills:
  - skill{s=
    [
      - setvariable{var=skill.temp;type=STRING;val=glow} @self
      - setvariable{var=skill.testskill;type=STRING;
        val=
        [
          - message{m=hello} @World
          - message{m=world} @World
          - message{m=<skill.var.temp>} @World
        ]} @self
      - vskill{s=<skill.var.testskill>}
      - vskill{s=
        [
          - e:p{p=<skill.var.temp>} @selflocation{y=2}
        ]} @self
    ]} @self ~onInteract
```
![2024-08-17_17.54.14](uploads/81ec8a247b38cc3eba7daca275b46b03/2024-08-17_17.54.14.png)

## What is happening?
The variableskill mechanic is a very interesting one: it executes the metaskill it finds in its `skill` attribute after parsing its content. While this is normally used only to execute metaskills whose name can depend on specifics of the mob or environment at the moment of the execution (making it very useful for templating) this also has an unexpected effect when combined with inline metaskills: as long as it's written as a inline metaskill, you can make the variableskill mechanic parse anything and expect it to get executed


# Dynamic Creation of Metaskills
And now, we come to the crux of the matter: you are now able to make completely new and unique metaskills on the spot without having to physically configure them
```yaml
Testmob:
  Type: pig
  Skills:
  - skill{s=
    [
      - setvariable{var=skill.temp;type=STRING;val=glow} @self
      
      - setvariable{var=skill.testskill2;type=STRING;val="["}
      - setvariable{var=skill.testskill2;type=STRING;val=<skill.var.testskill2> - message{m=aaa} @World} @self
      - setvariable{var=skill.testskill2;type=STRING;val=<skill.var.testskill2> - message{m=bbb} @World} @self
      - setvariable{var=skill.testskill2;type=STRING;val=<skill.var.testskill2>]} @self
      
      - vskill{s=<skill.var.testskill2>}
      - vskill{s=
        [
          - e:p{p=<skill.var.temp>} @selflocation{y=2}
        ]} @self
    ]} @self ~onInteract
```

# Bypassing Placeholder Support Limits
Not every attribute of every mechanic, condition or targeter has support for placeholders. This is often a limiting factor for a lot of advanced projects. But not anymore!  
Let's look at the examples above: at the time of writing the particle mechanic does not have placeholder support for its particle attribute, and yet that works when used with the methods described here. How come?
By using the setvariable mechanic to write the particle mechanic one can delegate the job of parsing the value of the attribute to the setvariable mechanic, which *has* placeholder support for the value attribute. The resulting string can then be executed via the variableskill mechanic.

One must then note that this operation is not exclusive to mechanic's attribute: you can literally use placeholders for *every single character* of the string that is being built, and as long as the result after parsing can then be considered a proper inline metaskill it will work!


# Storing Dynamic Metaskills
As you already saw, the newly made metaskill is being stored inside a variable. The variable can have any scope you deem fit, persist for as long as you want and have all the other cool stuff variables have. You can also store these skills inside NBTs, making items of your making being able to have completely custom skills for them

<!-- LINKS -->
[variableskill mechanic]: /skills/mechanics/variableskill
[variableskill]: /skills/mechanics/variableskill
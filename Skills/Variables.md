Variables
-----------------

Variables are a system for storing information. Using the variables system, you can store and manipulate values that you can use in placeholders or conditions later. These values can be either permanent or temporary.

### Variable Types

Variables can be one of several types, which is defined when the variable is initialized using the
[setVariable](/skills/mechanics/setvariable) mechanic. Types are generally interchangeable and MythicMobs will do its best to apply certain variables to whatever situation is asked, however it will throw
an error if you try to use a variable type for something that makes no sense.

**Current Types**:

| **Type** | **Description**                  |
|----------|----------------------------------|
| INTEGER  | A number with no decimal places. |
| FLOAT    | A number with decimal places.    |
| STRING   | A word or sentence.              |

### Variable Scopes

A variable's "scope" is **where** that variable exists. Not all scopes are applicable for all situations (e.g. a condition may not have a caster, rather the caster is the target of the condition).  

**Variable Scopes**:

| **Type** | **Where the Variable Exists**                                                                                  |
|----------|----------------------------------------------------------------------------------------------------|
| SKILL    | On the current skill tree. Always temporary and will vanish when the current queue of skills ends. |
| CASTER   | On the casting mob.                                                                                |
| TARGET   | On the target of the mechanic/condition.                                                           |
| WORLD    | The current world.                                                                                 |
| GLOBAL   | The server.                                                                                        |


### Usage

All variable mechanics and conditions accept **var=** and **scope=** attributes to determine what variable you're wanting to work with and where. You can also shorthand the scope using *var=scope.variable\_name**. The following examples would return the same thing:
```
    setvariable{var=target.somevariable; ...}
    setvariable{var=somevariable;scope=target; ...}
```

### Variable Mechanics

Variable mechanics are special mechanics that utilize variables. They can target entities, locations, or nothing, but the target can affect the outcome depending on what scope you're using. For example, trying to get a target-scope'd variable will obviously fail if you're not targeting an entity.

| Mechanic                                               | Description                                      |
|--------------------------------------------------------|--------------------------------------------------|
| [SetVariable](/skills/mechanics/setvariable)           | Initializes and sets a variable.                 |
| [SetVariableLocation](/skills/mechanics/setvariablelocation)   | Sets a variable, whose value depends on the target location.                 |
| [VariableUnset](/skills/mechanics/variableunset)           | Unsets the variable.                 |
| [VariableAdd](/skills/mechanics/variableadd)           | Adds to a numeric variable.                      |
| [VariableSubtract](/skills/mechanics/variablesubtract) | Subtracts from a numeric variable.               |
| [VariableMath](/skills/mechanics/variablemath)         | Lets you do calculations with numeric variables. |

### Variable Conditions

| Condition                                        | Description                                    |
|--------------------------------------------------|------------------------------------------------|
| [Variable Equals](/skills/conditions/variableequals)    | Checks if a variable equals a given value.     |
| [Variable Is Set](/skills/conditions/variableisset)     | Checks if a variable is set.                   |
| [Variable In Range](/skills/conditions/variableinrange) | Checks if a number variable is within a range. |

### Variable Placeholders

Variables can be referenced in any MythicMobs mechanics or values that allow placeholders. This is usually done using the format **&lt;scope.var.\[variable\]&gt;**.

When using placeholder variables, you can also specify a "default" value that will be used if the variable is undefined by using the syntax **&lt;scope.var.\[variable\]\|\[default\]&gt;**.

    message{m="Hello there, <target.var.title|wanderer>"} @trigger ~onInteract

In this example, the NPC would reply with "Hello there, wanderer" if
right-clicked by somebody who had no "title" variable set on them.
However, if we did this:

    setVariable{var=target.title;value="Sir"} @trigger ~onInteract

...somewhere along the line, even with a different mob, the first mob
would say "Hello there, Sir".
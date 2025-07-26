Variables are a system for storing information. Using the variables system, you can store and manipulate values that you can use in placeholders or conditions later. These values can be either permanent or temporary.

[[_TOC_]]

# Variable Types
Variables can be one of several types, which is defined when the variable is initialized using the
[setVariable](/skills/mechanics/setvariable) mechanic. Types are generally interchangeable and MythicMobs will do its best to apply certain variables to whatever situation is asked, however it will throw
an error if you try to use a variable type for something that makes no sense.

| **Type** | **Description**                  |
|----------|----------------------------------|
| INTEGER  | A number with no decimal places. |
| FLOAT    | A number with decimal places.    |
| DOUBLE   | A number with decimal places. Can represent much larger numbers than a FLOAT | 
| STRING   | A word or sentence.              |
| BOOLEAN  | A value that can either be true or false |
| SET      | A set of unordered and unique values |
| LIST     | An ordered list of entries       |
| MAP      | A list of key-value pairs        |
| LOCATION | A location in the server         |
| VECTOR   | A list composed of 3 DOUBLE values |
| TIME     | A moment in time, represented by the number of milliseconds since the epoch |


# Variable Scopes
A variable's "scope" is **where** that variable exists. Not all scopes are applicable for all situations (e.g. a condition may not have a caster, rather the caster is the target of the condition).  

| **Scope**| **Where the Variable Exists**                                                               |
|----------|---------------------------------------------------------------------------------------------|
| SKILL    | On the current skill tree. Always temporary and will vanish when the current queue of skills ends. |
| CASTER   | On the casting mob.                                                                                |
| TARGET   | On the target of the mechanic/condition.                                                           |
| WORLD    | The current world.                                                                                 |
| GLOBAL   | The server.                                                                                        |


# Usage
All variable mechanics and conditions accept `var=` and `scope=` attributes to determine what variable you're wanting to work with and where. You can also shorthand the scope using `var=scope.variable_name`. The following examples would return the same thing:
```yaml
    - setvariable{var=target.somevariable; ...}
    - setvariable{var=somevariable;scope=target; ...}
```

## Variable Types Behavior

### Number
Includes INTEGER, FLOAT and DOUBLE since their behavior is functionally the same
```yaml
  # Create your number variable
  - setvariable{var=skill.example;type=DOUBLE;val=1.5}

  # Add a value to a number
  - variableadd{var=skill.example;amount=2}

  # Remove a value from a number
  - variablesubtract{var=skill.example;amount=1}

  # Print a number
  - message{m=<skill.var.example>} # 2.5
```

### String
```yaml
  # Create your string variable
  - setvariable{var=skill.example;type=STRING;val="oh oh hello"}

  # append a value to a string
  - variableadd{var=skill.example;amount=" world"}

  # Remove every substring from a string
  - variablesubtract{var=skill.example;amount="oh oh "}

  # Print a string
  - message{m=<skill.var.example>} # hello world
```

### Boolean
```yaml
  # Create your boolean variable
  - setvariable{var=skill.example;type=BOOLEAN;val=true} # can also be "1" or "yes" for "true". Every other value is "false"

  # Performs an OR logical operation on the boolean
  - variableadd{var=skill.example;amount=1} # Sets the boolean to true if either current or added value is truthy (OR logic)

  # Performs an AND logical operation on the boolean
  - variablesubtract{var=skill.example;amount=1} # Sets the boolean to true only if both current and added value are truthy (AND logic)

  # Print a boolean
  - message{m=<skill.var.example>} # true
```

### Set
```yaml
  # Create a set
  - setvariable{var=skill.example;type=SET;val=1,2,hello}

  # Add a value to a set
  - variableadd{var=skill.example;amount=world}
  - variableadd{var=skill.example;amount=1} # If you add a value that is already present, the set will not change

  # Remove a value from a set
  - variablesubtract{var=skill.example;amount=hello}

  # Print a set
  - message{m=<skill.var.example>} # 1,2,world
```

### List
```yaml
  # Create a list
  - setvariable{var=skill.example;type=LIST;val=1,2,hello}

  # Add a value to a list
  - variableadd{var=skill.example;amount=world}

  # Remove a value from a list (using its index)
  - variablesubtract{var=skill.example;amount=0}

  # Print a list
  - message{m=<skill.var.example>} # 2,hello,world
  - message{m=<skill.var.example.0>} # 2
```

### Map
```yaml
  # Create a map
  - setvariable{var=skill.example;type=MAP;val="hello=world;mamma=mia"}

  # Add a value to a map
  - variableadd{var=skill.example;amount="pizza=pasta;please=help"}

  # Remove a value from a map(using its key)
  - variablesubtract{var=skill.example;amount=hello}

  # Print a map
  - message{m=<skill.var.example>} # mamma=mia;pizza=pasta;please=help
  - message{m=<skill.var.example.please>} # help
```

### Location
```yaml
  # Create your location variable
  - setvariable{var=skill.example;type=LOCATION;val=world,1,2,3}
  - setvarloc{var=skill.specialexample;val=@selflocation} # You can also set a location variable via this special mechanic

  # Increase the coordinates values
  - variableadd{var=skill.example;amount=1,2,3}

  # Decrease the coordinates values
  - variablesubtract{var=skill.example;amount=1,1,1}

  # Print a location
  - message{m=<skill.var.example>} # world,1.0,3.0,5.0
```

### Vector
```yaml
  # Create your vector variable
  - setvariable{var=skill.example;type=VECTOR;val=1,2,3}

  # Increase the component values
  - variableadd{var=skill.example;amount=1,2,3}

  # Decrease the component values
  - variablesubtract{var=skill.example;amount=1,1,1}

  # Print a location
  - message{m=<skill.var.example>} # 1.0,3.0,5.0
```

### Time
```yaml
  # Create your time variable
  - setvariable{var=skill.example;type=TIME;val=1234}

  # Increase the value
  - variableadd{var=skill.example;amount=2}

  # Decrease the value
  - variablesubtract{var=skill.example;amount=1}

  # Print a time
  - message{m=<skill.var.example>} # 1235
```


## Variable Mechanics
Variable mechanics are special mechanics that utilize variables. They can target entities, locations, or nothing, but the target can affect the outcome depending on what scope you're using. For example, trying to get a target-scoped variable will obviously fail if you're not targeting an entity.

| Mechanic                                               | Description                                      |
|--------------------------------------------------------|--------------------------------------------------|
| [SetVariable](/skills/mechanics/setvariable)           | Initializes and sets a variable.                 |
| [SetVariableLocation](/skills/mechanics/setvariablelocation)   | Sets a variable, whose value depends on the target location.                 |
| [VariableUnset](/skills/mechanics/variableunset)           | Unsets the variable.                  |
| [VariableAdd](/skills/mechanics/variableadd)           | Adds to a  variable.                      |
| [VariableSubtract](/skills/mechanics/variablesubtract) | Subtracts from a  variable.               |
| [VariableMath](/skills/mechanics/variablemath)         | Lets you do calculations with numeric variables. |

## Variable Conditions
| Condition                                        | Description                                    |
|--------------------------------------------------|------------------------------------------------|
| [VariableEquals](/skills/conditions/variableequals)    | Checks if a variable equals a given value.    |
| [VariableIsSet](/skills/conditions/variableisset)     | Checks if a variable is set.                   |
| [VariableInRange](/skills/conditions/variableinrange) | Checks if a number variable is within a range. |
| [VariableContains](/skills/conditions/VariableContains) | Checks if a variable contains a given value. |

## Variable Targeters
| Targeter                                         | Description                                    |
|--------------------------------------------------|------------------------------------------------|
| @[VariableLocation](/Skills/Targeters/VariableLocation) | Targets the location stored in the specified Location variable. |


# Variable Placeholders
Variables can be referenced in any MythicMobs mechanics or values that allow placeholders. This is usually done using the format `<scope.var.variable>`.

Variable Placeholders can also use Meta Keywords to change the output of the placeholder, and they can even chain Meta Keywords together to obtain a "compound" effect.

Find out more on the [Meta Variable Placeholder Explanation](/Skills/Placeholders#meta-variable-placeholders)

# Variable Fallback
When using placeholder variables, you can also specify a "default" value that will be used if the variable is undefined by using the syntax `<scope.var.variable|default>`.

```yaml
    - message{m="Hello there, <target.var.title|wanderer>"} @trigger ~onInteract
```

In this example, the NPC would reply with "Hello there, wanderer" if
right-clicked by somebody who had no "title" variable set on them.
However, if we did this:

```yaml
    - setVariable{var=target.title;value="Sir"} @trigger ~onInteract
```

...somewhere along the line, even with a different mob, the first mob
would say "Hello there, Sir".

# Nested Variable
Variables can also be nested indefinitely: if this is done, the innermost variable would be resolved first and, from there, each would be resolved from innermost to outermost

```yaml
  Skills:
    - setvariable{var=caster.hello;type=STRING;val=example_name} @self
    - setvariable{var=caster.example_name;type=STRING;val=Hello There!} @self
    - message{m="<caster.var.<caster.var.hello>>"} @PIR{r=10}
```
> In this example, the message would spell "Hello there!"

# [Mob Variables](/Mobs/Mobs#variables)
Mobs can have some variable be already set once they spawn thanks to the [Mob Variables](/Mobs/Mobs#variables) field.
```yaml
VariableZombie:
     Type: ZOMBIE
     Variables:
       SomeVariable: something
       AnIntVariable: int/2
       AFloatVariable: float/420.69
```
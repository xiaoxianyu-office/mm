Lets you make simple or advanced calculations. Any placeholders that returns a number is supported.
You can use math in most places that supports placeholders.

[[_TOC_]]

## Operators
Most of these operators can be found here https://www.objecthunter.net/exp4j/#Built-in_operators
### Math Operators

| Operator |   Description    |  Example  |
|:--------:|:----------------:|:---------:|
|    +     |    Unary plus    |   2 + 2   |
|    -     |   Unary minus    |   2 - 2   |
|    *     |  Multiplication  |   2 * 2   |
|    /     |     Division     |   2 / 2   |
|    ^     |      Power       |   2 ^ 2   |
|    %     |    Remainder     |   2 % 2   |

### Boolean Operators
| Operators |       Description        | Example |
|:---------:|:------------------------:|:-------:|
|    \<     |        Less than         |   2<5   |
|    \<=    |  Less than or equal to   |  2<=5   |
|    \>     |       Greater than       |   5>1   |
|    \>=    | Greater than or equal to |  5>=0   |
|    \==    |          Equals          |  0==0   |

*Boolean operators will return `1` if the expression is true and `0` if it's false.*


## Functions
Most of these functions can be found here https://www.objecthunter.net/exp4j/#Built-in_functions

|     Function     | Description                                                     |
|:----------------:|:----------------------------------------------------------------|
|      abs(x)      | the absolute value of (x)                                       |
|     acos(x)      | arc cosine                                                      |
|     asin(x)      | arc sine                                                        |
|     atan(x)      | arc tangent                                                     |
|     cbrt(x)      | cubic root                                                      |
|     ceil(x)      | nearest upper integer                                           |
|      cos(x)      | cosine                                                          |
|     csch(x)      | hyperbolic cosecant                                             |
|      exp(x)      | euler's number raised to the power (e^x)                        |
|     floor(x)     | nearest lower integer                                           |
|      log(x)      | logarithmus naturalis (base e)                                  |
|     log2(x)      | logarithm to base 2                                             |
|     log10(x)     | logarithm to base 10                                            |
|     logb(x)      | logarithm to base b                                             |
|      sec(x)      | secant                                                          |
|     sech(x)      | hyperbolic secant                                               |
|      sin(x)      | sine                                                            |
|     sinh(x)      | hyperbolic sine                                                 |
|     sqrt(x)      | square root                                                     |
|      tan(x)      | tangent                                                         |
|     tanh(x)      | hyperbolic tangent                                              |
|    signum(x)     | signum of a value                                               |
|   toradian(x)    | converts from degrees to radians                                |
|   todegree(x)    | converts from radians to degrees                                |
|    min(x, y)     | minimum                                                         |
|    max(x, y)     | maximum                                                         |
|   atan2(y, x)    | principal value of the arc tangent of y/x, expressed in radians |
| random(min, max) | random with limits                                              |
| clamp(value, min, max) | Clamps a number between a given minimum and maximum. If the number you provide is less than the minimum, it will return the minimum. If it's greater than the maximum, it returns the maximum. If it's between the minimum and maximum, it returns the number unchanged |

NOTE: You can request to add more operators and functions by making a suggestion ticket in our [issues page](https://git.mythiccraft.io/mythiccraft/MythicMobs/-/issues)


## Example Usage
```yml
MyCoolMob:
  Type: HUSK
  AIGoalSelectors:
    - clear
  AITargetSelectors:
    - clear
  Skills:
    - skill{s=[
      - setvar{var=skill.test;type=FLOAT;val="<caster.hp> <= <caster.mhp>"} #returns 1 or 0 if the mob's health is less than or equal to its max health
      - message{m=<skill.var.test>} #sends the player a message to see the value
      ]} @trigger ~onInteract
```

```yml
MyCoolItem:
  Id: STICK
  Skills:
    - skill{s=[
        - setvar{var=skill.test;type=FLOAT;val="1>=0"} #returns 1 since the expression evaluates to true
        - message{m=<skill.var.test>} #sends the player a message to see the value
      ]} @Self ~onUse
```
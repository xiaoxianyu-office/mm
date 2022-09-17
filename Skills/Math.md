Lets you make simple or advanced calculations. Any placeholders that returns a number is supported.
You can use math in most places that supports placeholders.

Operators
-----------
Most of these operators can be found here https://www.objecthunter.net/exp4j/#Built-in_operators
#### Math Operators

| Operator |   Description    |  Example  |
|:--------:|:----------------:|:---------:|
|    +     |    Unary plus    |   2 + 2   |
|    -     |   Unary minus    |   2 - 2   |
|    *     |  Multiplication  |   2 * 2   |
|    /     |     Division     |   2 / 2   |
|    ^     |      Power       |   2 ^ 2   |
|    %     |    Remainder     |   2 % 2   |

#### Boolean Operators
| Operators |       Description        | Example |
|:---------:|:------------------------:|:-------:|
|    \<     |        Less than         |   2<5   |
|    \<=    |  Less than or equal to   |  2<=5   |
|    \>     |       Greater than       |   5>1   |
|    \>=    | Greater than or equal to |  5>=0   |
|    \==    |          Equals          |  0==0   |
*Boolean operators will return `1` if the expression is true and `0` if it's false.*


Functions
---------
Most of these functions can be found here https://www.objecthunter.net/exp4j/#Built-in_functions

| Functions                                                       |     Example      |
|:----------------------------------------------------------------|:----------------:|
| the absolute value of (x)                                       |      abs(x)      |
| arc cosine                                                      |     acos(x)      |
| arc sine                                                        |     asin(x)      |
| arc tangent                                                     |     atan(x)      |
| cubic root                                                      |     cbrt(x)      |
| nearest upper integer                                           |     ceil(x)      |
| cosine                                                          |      cos(x)      |
| hyperbolic cosecant                                             |     csch(x)      |
| euler's number raised to the power (e^x)                        |      exp(x)      |
| nearest lower integer                                           |     floor(x)     |
| logarithmus naturalis (base e)                                  |      log(x)      |
| logarithm to base 2                                             |     log2(x)      |
| logarithm to base 10                                            |     log10(x)     |
| logarithm to base b                                             |     logb(x)      |
| secant                                                          |      sec(x)      |
| hyperbolic secant                                               |     sech(x)      |
| sine                                                            |      sin(x)      |
| hyperbolic sine                                                 |     sinh(x)      |
| square root                                                     |     sqrt(x)      |
| tangent                                                         |      tan(x)      |
| hyperbolic tangent                                              |     tanh(x)      |
| signum of a value                                               |    signum(x)     |
| converts from degrees to radians                                |   toradian(x)    |
| converts from radians to degrees                                |   todegree(x)    |
| minimum                                                         |    min(x, y)     |
| maximum                                                         |    max(x, y)     |
| principal value of the arc tangent of y/x, expressed in radians |   atan2(y, x)    |
| random with limits                                              | random(min, max) |

NOTE: You can request to add more operators and functions by making a suggestion ticket in our [issues page](https://git.mythiccraft.io/mythiccraft/MythicMobs/-/issues)
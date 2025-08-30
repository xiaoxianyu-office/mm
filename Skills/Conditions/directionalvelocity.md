## Description
A condition that checks checks if the target has a velocity matching the given parameters.


## Attributes
| Attribute | Aliases   | Description                                                          | Default |
|-----------|-----------|----------------------------------------------------------------------|---------|
| x         | s, side   | The X velocity. Can be a range. Isn't checked by the condition if not set  |   |
| absx      | ax, abss, as | Whether to use only the absolute values for the X velocity        | `relative`'s value|
| y         | up, down, vertical, v | The Y velocity. Can be a range. Isn't checked by the condition if not set |   |
| absy      | ay        | Whether to use only the absolute values for the Y velocity           |  false  |
| z         | f, forward| The Z velocity. Can be a range. Isn't checked by the condition if not set  |   |
| absz      | az, absf, af | Whether to use only the absolute values for the Z velocity        |  false  |
| relative  | rel | Whether the check should be relative to the entity's orientation and not to the world axis. If true, X is forward/backward and Z is side-to-side                                     |  false  |

### X, Y and Z Attributes
They check against the velocity of the entity along those axis. But this also means that the velocity itself can be either positive or negative depending on the direction itself. 
> - If you are moving **towards `positive` X values**, you will have a **`positive` X velocity**.
> - If you are moving **towards `negative` X values**, you will have a **`negative` X velocity**
> - If you are **jumping `up`**, you will have **`positive` Y velocity**
> - If you are **falling `down`**, you will have **`negative` Y velocity**

### Absx, Absy and Absz Attributes
Despite the former, you may not want to check against the *direction* of the movement, but its *magnitude*. For that, you have to enable those attributes, and once you do their respective X, Y or Z attribute will only check against absolute values (will be positive regardless of the actual direction)
> - If you are **jumping `up`**, you will have **`positive` Y velocity**
> - If you are **falling `down`**, you will have **`positive` Y velocity**


## Examples
In this example, we check if the players y velocity is under an absolute value of 5.
```yaml
  Conditions:
  - directionalVelocity{y=<0;absx=true} true
```


## Aliases
- [x] dvelocity
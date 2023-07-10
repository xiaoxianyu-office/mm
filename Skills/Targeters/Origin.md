## Description
Targets the location of the "origin" or "source" of a meta-skill. While that is usually the casting mob, there are special cases where this is not true (such as with the Projectile Skill, where the "origin" is the location of the projectile)


## Attributes
>*This targeter has no attributes*


## Examples
The origin targeter is extremely versatile. Take the following metaskill, for instance:
```yaml
ExampleSkill:
  Skills:
  - effect:particles @origin
```
If it is executed by a mob normally, if will display the particles at its location, since the origin of the skill is itself. In this aspect, `origin` does not behave differently from a `self` targeter.  

But if the metaskill is executed inside a meta mechanic or after manually changing a skill's origin via the [Origin Universal Attribute](/Skills/Mechanics#universal-attributes), the origin of the skill will change most of the times, and the particles will be displayed in a different spot.  

The exact position of the `origin` changes based on the context, and more information regarding this behavior can be found in wiki pages for the various mechanics that *do* make use of this.

## Aliases
- [x] source
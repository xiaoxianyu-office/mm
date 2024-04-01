Causes the current skill or mechanic to be delayed by X ticks.

Delay can also be used as an attribute directly inside of mechanics by adding `delay=TICKS`, see example below.

Skill-delay and Attribute-delay do not function the same manner.

# Examples

```yaml
Skills:
  - ignite{ticks=60}
  - delay 60
  - explode
```

This is an example of using the delay universal attribute. It will work inside any mechanic and will delay it from happening by the specified amount of ticks.
```yaml
Skills:
  - skill{skill=exampleskill;delay=200}
  - explode{delay=80}
```
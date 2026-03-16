| Scope     | Target Entity               |
|-----------|-----------------------------|
| `caster`  | The caster of the mechanic  |
| `target`  | The target of the mechanic.<br>For instance `- message{m=<target.name>} @NearestPlayer` will message their nearest player their own name  |
| `trigger` | The trigger of the mechanic, the entity that caused the skill to happen.<br>For instance `<trigger.name>` combined with an `~onDeath` trigger will return the name of the entity that killed the mob |
| `owner`  | The owner of the casting entity  |
| `parent`  | The parent of the casting entity  |

Templates are a functionality that allows a mob to "inherit" the characteristics of one or more other mobs.

If you are already familiar with Object Oriented Programming, you will then probably find the following quite similar to the concept of Inheritance.

But regardless, Template may still be found to be quite complicated to understand at first. As such, we will be adding more nuanche to the concept as we go on explaining it, starting from the very basics and gettings to the more complex use cases.

[[_TOC_]]

## Introduction
As already stated, Templates allows a mob to inherit the characteristics of another. But what does this even mean?

To explain it in simpler terms, we will present, as an example, a mob:
```yaml
ZombieBrute:
  Type: ZOMBIE
  Display: "&2Zombie Brute &7[Lv. <caster.level>]&r"
  Health: 30
  Damage: 5
  Faction: Monster
  Equipment:
  - Iron_Helmet HEAD
  - Iron_Chestplate CHEST
  - Iron_Leggings LEGS
  - Iron_Boots FEET
  - Shield OFFHAND
  Drops:
  - exp 10-15 1
  - rotten_flesh 1-2 1
  - ZombieBrute_Hearth 1 0.01
  Options:
    AlwaysShowName: true
    PreventOtherDrops: true
    PreventRandomEquipment: true
    PreventSunburn: true
    PreventItemPickup: true
    PreventJockeyMounts: true
    PreventTransformation: true
  AITargetSelectors:
  - clear
  - attacker
  - players
  AIGoalSelectors:
  - clear
  - meleeattack
  - randomstroll
  DamageModifiers:
  - PROJECTILE 1.15
  - ENTITY_ATTACK 0.75
  KillMessages:
  - '<target.name> was reduced to paste by a <caster.name>'
  - 'Despite his best efforts, <target.name> could not prevail against a <caster.name>'
  - '<target.name> was killed by a <caster.name>'
  Skills:
  - skill{s=SelectRandomWeapon} @self ~onSpawn
  - skill{s=ZombieBrute_Bash} @target ~onTimer:60 0.4 ?targetwithin{d=10}
  - skill{s=CallZombies} @EIR ~onTimer:180 0.6
```
That, while not complex to make, certainly has quite a number of elements associated with it, hasn't he? He's got a Faction, some Drops, some Options...

Now, what if we wanted to create another mob that shares some (if not most!) of the characteristics this mob has? We would normally need to copy-paste what we want from one mob to another, and while that works on the short term, what if we want to later *modify* those characteristics? We would need to track down every instance of them being present on some mob and then change those, one by one. That has no scalability whatsoever!

But here, Templates comes to the rescue: remember what we said originally? They allows to inherit characteristics across mobs, and so, we would need to only make one mob that has all of those common characteristics, and if we want to change some of them at a later date, instead of going mob-by-mob, we could just modify that one mob and see the change being automatically applied to any mob that uses it as a template!

And that brings us to our first, real example of using templates.

## Single Template
Let's say that we want to make a group of mobs share the Factions, the Options, the Ai, some of the Skills and some other element from ZombieBrute. First, we put those elements into a mob
```yaml
MonsterFaction_Base:
  Type: ZOMBIE
  Faction: Monster
  Drops:
  - exp 10-15 1
  Options:
    AlwaysShowName: true
    PreventOtherDrops: true
    PreventRandomEquipment: true
    PreventSunburn: true
    PreventItemPickup: true
    PreventJockeyMounts: true
    PreventTransformation: true
  AITargetSelectors:
  - clear
  - attacker
  - players
  AIGoalSelectors:
  - clear
  - meleeattack
  - randomstroll
  DamageModifiers:
  - PROJECTILE 0.75
  - ENTITY_ATTACK 0.75
  KillMessages:
  - '<target.name> was killed by a <caster.name>'
  Skills:
  - skill{s=SelectRandomWeapon} @self ~onSpawn
```
And once we do that, let's make the (now slimmer) ZombieBrute inherit those
```yaml
ZombieBrute:
  Template: MonsterFaction_Base
  Display: "&2Zombie Brute &7[Lv. <caster.level>]&r"
  Health: 30
  Damage: 5
  Equipment:
  - Iron_Helmet HEAD
  - Iron_Chestplate CHEST
  - Iron_Leggings LEGS
  - Iron_Boots FEET
  - Shield OFFHAND
  Drops:
  - rotten_flesh 1-2 1
  - ZombieBrute_Hearth 1 0.01
  DamageModifiers:
  - PROJECTILE 1.15
  KillMessages:
  - '<target.name> was reduced to paste by a <caster.name>'
  - 'Despite his best efforts, <target.name> could not prevail against a <caster.name>'
  Skills:
  - skill{s=ZombieBrute_Bash} @target ~onTimer:60 0.4 ?targetwithin{d=10}
  - skill{s=CallZombies} @EIR ~onTimer:180 0.6
```
And there! With just a simple line, `Template: MonsterFaction_Base`, is now being Inherited by `ZombieBrute`, with any elements contained in `MonsterFaction_Base` now being automatically inherited by `ZombieBrute`

```mermaid
flowchart TD
    A[MonsterFaction_Base] -->|Is Inherited by| B[ZombieBrute]
```

But what about elements that are present on both the mob and its template?

### Shared Elements
When both the Mob and its Template share some elements, those are inherited in different ways depending on the *value* of the element in question.

The *value* of the element generally falls into one of three categories:
- The value is a `string`
- The value is a `list` of strings
- The value are other `elements`

#### String Value
```yaml
TemplateMob:
  Type: ZOMBIE
  Faction: TemplateFaction

ExampleMob:
  Template: TemplateMob
  Faction: ExampleFaction
```
This is the easiest to understand: when an element with a string value is inherited from a template (`TemplateMob`) to a mob (`ExampleMob`) that **also has the same element**, then the element is **overridden** 

> So, when you spawn `ExampleMob`, its `Faction` will be `ExampleFaction`, since the mob's element has overridden the template's 

#### List Value
```yaml
TemplateMob:
  Type: ZOMBIE
  KillMessages:
  - <caster.name> yeeted <target.name>!!

ExampleMob:
  Template: TemplateMob
  KillMessages:
  - You're too weak <target.name>!!
```

When an element with a *list* of strings as its value is inherited from a template (`TemplateMob`) to a mob (`ExampleMob`) that **also has the same element**, then the element is **merged**

This means that the resulting element will have **all** of the strings that made up the original lists, concatenated

> So, when you spawn `ExampleMob`, its `KillMessages` will be
> ```yaml
> - <caster.name> yeeted <target.name>!!
> - You're too weak <target.name>!!
> ```
> in this exact order

##### Order in List Values

There are instances where the *order* of inheritance matters a lot: for instance, if there is a list of instructions or a list of key-value pairs. For these situations, you must always remember that, usually, **lists are parsed from top to bottom**, so *instructions are parsed in that order*, and *in key-value lists, the bottom-most "wins out"*

For instance, let's take the following example with some AI Goals

```yaml
TemplateMob:
  Type: ZOMBIE
  AIGoalSelectors:
  - clear
  - meleeattack

ExampleMob:
  Template: TemplateMob
  AIGoalSelectors:
  - clear
  - randomstroll
```

Given this situation, the end result will be
```yaml
  - clear
  - meleeattack
  - clear
  - randomstroll
```

Which does look a bit odd. But worry not! Even in situations as peculiar as this one, there is always an underlying logic. For instance, here the `clear` goal clears everything that was before it. So, we effectively get 
```yaml
  - clear
  - randomstroll
```

Another such instance is with DamageModifiers
```yaml
TemplateMob:
  Type: ZOMBIE
  DamageModifiers:
  - ENTITY_ATTACK 1
  - PROJECTILE 1

ExampleMob:
  Template: TemplateMob
  DamageModifiers:
  - ENTITY_ATTACK 0.5
```

Where, after the merge, the resulting list would be
```yaml
  - ENTITY_ATTACK 1
  - PROJECTILE 1
  - ENTITY_ATTACK 0.5
```

In which case, among multiple modifiers with the same name, only the *bottom-most* is ultimately counted. Meaning, the above can be rewritten as
```yaml
  - PROJECTILE 1
  - ENTITY_ATTACK 0.5
```

#### Elements Value
```yaml
TemplateMob:
  Type: ZOMBIE
  Options:
    FollowRange: 32
    Despawn: true
    Glowing: false

ExampleMob:
  Template: TemplateMob
  Options:
    FollowRange: 16
```
These are elements that, as a value, have other elements! Still, they do not behave like other elements with a "proper" value do.

You can imagine the situation with "Elements that have other elements as values" being a sort of `folder`, and with the "Elements that have string or list values" being a sort of `file`. When you merge two folders, what happens is that *all files are kept*, **except** for those files that share the same name and folder.

The same things happens here!

For instance, `TemplateMob` has an `Option` element that, itself, has both a `FollowRange` element and a `Despawn` one. When `ExampleMob` inherits from `TemplateMobs`, *all options* are kept, **except** for `FollowRange`, which is in both `TemplateMob.Options` and in `ExampleMob.Options`.

Now, what happens for it?  
Well, `FollowRange` is an element with a string value, so it behaves like any other [Element with a string value](#string-value)!  
Similarly, elements in here that have a list value also behaves [like their counterparts](#list-value)

#### Examples

To make this more understandable, the following is a *non-exhaustive* list of some of the elements a Template may have and how the Mob will inherit them if the Mob has them too. 

| **Element** *(in the Template)*       | **How it is inherited** *(if the Mob has it too)*              |
|---------------------------------------|----------------------------------------------------------------| 
| Type                                  | Overridden                                                     |
| Display                               | Overridden                                                     |
| Health                                | Overridden                                                     |
| Damage                                | Overridden                                                     |
| Armor                                 | Overridden                                                     |
| Bossbar                               | Overridden                                                     |
| Faction                               | Overridden                                                     |
| Mount                                 | Overridden                                                     |
| Options                               | Partially Overridden (only the shared options are overridden)  |           
| Modules                               | Partially Overridden (only the shared modules are overridden)  |
| AIGoalSelectors                       | Merged*                                                        |
| AITargetSelectors                     | Merged*                                                        |
| Drops                                 | Merged                                                         |
| DamageModifiers                       | Partially Overridden (only the shared modifiers are overridden)|
| Equipment                             | Partially Overridden (only equipment with the same slot is overridden)|
| KillMessages                          | Merged                                                         |
| LevelModifiers                        | Partially Overridden (only the shared modifiers are overridden)|
| Disguise                              | Overridden                                                     |
| Skills                                | Merged                                                         |
| Trades                                | Partially Overridden (only trades with the same number are overridden)|


\* A special note must be made regarding the behavior of the AIGoalsSelector and the AITargetSelectors elements, as only stating that they are "merged" is a bit reductive. The selector of the Mob are, in fact, added to the end of the Template's. So, for instance, if the Template has a `clear`,`meleeattack` AIGoals and the Mob has a `randomstroll` one, the final mob will effectively have `clear`,`meleeattack`,`randomstroll` as its AIGoals.
If one wishes to reset the Selectors from the Template, one can either use the [`Exclude`](#excluding-elements) element or use the `clear` Selector, as that will "delete" every Selector that came before it.

### Excluding Elements
It is possible to stop a Mob from inheriting unwanted elements from its Template using the following syntax
```yaml
  Exclude:
  - Element1
  - Element2
  - {...}
```

So, for instance, if we wanted a mob to not inherit the Equipment, the AITargetSelectors and the Skills, we would be using

```yaml
ExampleMob:
  Template: MobTemplate
  Exclude:
  - Equipment
  - AITargetSelectors
  - Skills
```
And the mob will now not inherit the specified elements.

## Chained Templates
But why should we stop at only one Template? After all, Templates can have a Template, too! Let's revisit out example from earlier, but this time splitting it up a little bit more

```yaml
MonsterFaction_Base:
  Type: ZOMBIE
  Faction: Monster
  Drops:
  - exp 10-15 1
  Options:
    AlwaysShowName: true
    PreventOtherDrops: true
    PreventRandomEquipment: true
    PreventSunburn: true
    PreventItemPickup: true
    PreventJockeyMounts: true
    PreventTransformation: true
  DamageModifiers:
  - PROJECTILE 0.75
  - ENTITY_ATTACK 0.75
  KillMessages:
  - '<target.name> was killed by a <caster.name>'
```

```yaml
MonsterFaction_MeleeEntity:
  Template: MonsterFaction_Base
  Equipment:
  - Iron_Helmet HEAD
  - Iron_Chestplate CHEST
  - Iron_Leggings LEGS
  - Iron_Boots FEET
  - Shield OFFHAND
  AITargetSelectors:
  - clear
  - attacker
  - players
  AIGoalSelectors:
  - clear
  - meleeattack
  - randomstroll
  Skills:
  - skill{s=SelectRandomWeapon} @self ~onSpawn

```

```yaml
ZombieBrute:
  Template: MonsterFaction_MeleeEntity
  Display: "&2Zombie Brute &7[Lv. <caster.level>]&r"
  Health: 30
  Damage: 5
  Drops:
  - rotten_flesh 1-2 1
  - ZombieBrute_Hearth 1 0.01
  DamageModifiers:
  - PROJECTILE 1.15
  KillMessages:
  - '<target.name> was reduced to paste by a <caster.name>'
  - 'Despite his best efforts, <target.name> could not prevail against a <caster.name>'
  Skills:
  - skill{s=ZombieBrute_Bash} @target ~onTimer:60 0.4 ?targetwithin{d=10}
  - skill{s=CallZombies} @EIR ~onTimer:180 0.6
```

This way, we have created a new mob, `MonsterFaction_MeleeEntity`, that is using `MonsterFaction_Base` as a Template.

And with `ZombieBrute` using `MonsterFaction_MeleeEntity` as a Template, it does not inherit the only elements of `MonsterFaction_MeleeEntity`, but also those that `MonsterFaction_MeleeEntity` itself inherited up to that point.

```mermaid
flowchart TD
    A[MonsterFaction_Base] -->|Is Inherited by| B[MonsterFaction_MeleeEntity] -->|Is Inherited by| C[ZombieBrute]
```

## Multi Templates
Up until now we have shown how to use a single Template inside of a mob, but a mob can use more than one at the same time.

By simply using a list of Templates as the Template argument, we can make the mob inherit one template after another **from the leftmost on the list to the rightmost**. Simply said, by making a list of templates, it's like we are chaining multiple templates together, starting from the leftmost one and ending with the rightmost one.

But let's see an example to make things clear:
```yaml
DiamondArmorSet:
  Type: ZOMBIE
  Equip:
  - Diamond_Helmet HEAD
  - Diamond_Chestplate CHEST
  - Diamond_Leggings LEGS
  - Diamond_Boots FEET
```
This mob does nothing in particular by itself, its only characteristic being the diamond set of armor it has equipped. But if we use it like so:

```yaml
ZombieBrute:
  Template: MonsterFaction_MeleeEntity, DiamondArmorSet
  Display: "&2Zombie Brute &7[Lv. <caster.level>]&r"
  Health: 30
  Damage: 5
  Drops:
  - rotten_flesh 1-2 1
  - ZombieBrute_Hearth 1 0.01
  DamageModifiers:
  - PROJECTILE 1.15
  KillMessages:
  - '<target.name> was reduced to paste by a <caster.name>'
  - 'Despite his best efforts, <target.name> could not prevail against a <caster.name>'
  Skills:
  - skill{s=ZombieBrute_Bash} @target ~onTimer:60 0.4 ?targetwithin{d=10}
  - skill{s=CallZombies} @EIR ~onTimer:180 0.6
```

Then our dear `ZombieBrute` now will spawn with a shiny new set of diamond armor, since the `DiamondArmorSet` Template is overriding some of the equipments present in `MonsterFaction_MeleeEntity`

```mermaid
flowchart TD
    A[MonsterFaction_Base] -->|Is Inherited by| B[MonsterFaction_MeleeEntity] --->|Is Inherited by| C[ZombieBrute]
    D[DiamondArmorSet]  --> |Is Inherited by| C[ZombieBrute]
```

---

## Item Templates
[Items](/Items/Items#template) can use Templating like mobs while referencing other items!
```yaml
MyItem:
  Template: MyOtherItem
```
```yaml
MyOtherItem:
  Template: YetAnotherItem, AndAnotherOne
```
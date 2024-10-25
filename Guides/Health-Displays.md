**Difficulty: Beginner**

You may want to display your mobs health to players who are fighting it, there are a few different ways of doing this and this guide will go over them!

# Boss Bars
You can create a Boss Bar for your mob and use it to display your mobs health much like the Ender Dragon or Wither has. The process is simple.
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  BossBar:
    Enabled: true
    Title: '&cSkeleton King!'
    Range: 50
    Color: GREEN
    Style: SEGMENTED_12
```

# Nameplate
You can display the mobs health in its nameplate above it, you can do this many different ways, here are 2 examples, one which shows the mobs health as a number (15/20) and another which has a bar that changes as the mob loses health.

### Number
You will need to use the [SetName](/skills/mechanics/setname) mechanic and the [~onDamaged](/Skills/Triggers/onDamaged) trigger. We will use the mobs display option to set the information. We are using the caster.hp and caster.mhp placeholders to get the current HP and the max HP.
```yaml
SkeletonKing:
  Type: WITHER_SKELETON
  Display: '&6Skeleton King &7(<caster.hp>/<caster.mhp>)'
  Skills:
  - setname{n=<caster.name>;delay=2} @self ~onDamaged
```
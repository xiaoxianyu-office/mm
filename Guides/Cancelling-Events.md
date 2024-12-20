**Difficulty: Beginner**

Most mob types have their own default way of doing things built into Minecraft, many of these actions can be blocked using the [CancelEvent](/skills/mechanics/cancelevent) mechanic, allowing you to replace a vanilla action with a custom one!

A common example is cancelling a mobs attack with ~onAttack and replacing it with your own attack skill instead.

Keep in mind that CancelEvent requires the `sync=true` universal attribute on the original mechanic, and not all triggers are supported, a list of avilable triggers can be found on the [CancelEvent](/skills/mechanics/cancelevent) mechanics page. You may also come across a few quirks with things such as cancelling a death to create a custom death event, or cancelling a damage event to create your own, which gets cancelled, and getting stuck in a loop, so tips for these situations can be found below.

# Attack
This is an example of cancelling a mobs attack and creating your own attack skill instead.

On your mob you would run this mechanic:

`- skill{s=FireAttack;sync=true} @target ~onAttack`

And in your skills file you'd create a MetaSkill like this:
```yaml
FireAttack:
  Skills:
  - cancelevent
  - damage{a=5}
  - ignite @target
```

You can also use the onShoot trigger for ranged mobs since they cannot have their default shoot modified, you can cancel it and create your own with mechanics such as [Projectile](/skills/mechanics/projectile) or [Shoot](/skills/mechanics/shoot)!

This example, if applied to a skeleton, would make it fire multiple arrows that deal more damage rather than its standard single arrow attack.

`- skill{s=ArrowVolley;sync=true} @target ~onShoot`

```yaml
ArrowVolley:
  Skills:
  - cancelevent
  - volley{type=EGG;velocity=5;damage=10;amount=20}
```

# Damage

You can cancel the damage event of a mob, either for making a mob invincible, or to modify the way it takes damage.

Making the mob invincible using this method is very straight forward, just add this to your mobs skills section

`- cancelevent{sync=true} @self ~onDamaged`

You can add to this using conditions, so that your mob is only invincible in certain scenarios, this example will make the mob invincible as long as the player attacks it with a diamond sword. This example uses an [In-Line Trigger Condition](/Skills/Inline-Conditions#conditions-triggerconditions)

`- cancelevent{sync=true} @self ~onDamaged ?~holding{m=DIAMOND_SWORD}`

This example below, will cancel all damage the mob receives, and replace it with a damage mechanic, which will make the mob always takes a specific amount of damage, regardless of weapon. Since we are cancelling the damage, and then damaging the mob directly, it will get stuck in a loop, so we will be using a damageTag and checking if the tag is present, if it is, then the damage won't be cancelled and the mob will be hurt.

`- skill{s=SelfDamage;sync=true} @self ~onDamaged`

```yaml
SelfDamage:
  Conditions:
  - damageTag{tag=SELFDAMAGE} false
  Skills:
  - cancelevent
  - damage{a=10;tag=SELFDAMAGE} @self
```

# Death

You may want to cancel the death event so you can create a custom death with fancy effects. We will need to remove the mob using the remove mechanic rather than it being removed from damage, so if you are cancelling the death keep in mind that onDeath skills won't work, and will need to be modified to be included here, things such as giving rewards etc.

`- skill{s=DeathSkill;sync=true} @self ~onDeath`

```yaml
DeathSkill:
  Skills:
  - cancelevent
  - delay 10
  - fakeexplosion @self
  - particlesphere{particle=flame;amount=200;radius=5;repeat=5;repeatinterval=5} @self
  - delay 20
  - remove @self
```
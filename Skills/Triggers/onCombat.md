## Description
The default trigger if none was used.  
Will execute when these events occurs:
- The mob deals damage
- The mob takes damage
- The mob spawns
- The mob dies


## Examples
```yml
SkeletalWarrior:
  Mobtype: skeleton
  Display: '<blue>A Skeletal Warrior</blue>'
  Skills:
  - skill{s=Bash} =10%-90%
```
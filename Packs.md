MythicMobs has a very powerful pack system to organize ALL your files better, and also get packs from Vendors through sources like MCModels installed very easily.

Simply make a folder inside the MythicMobs/Packs folder (name it whatever you want for your pack), and then inside of it you can make folders for Items, Mobs, Skills, RandomSpawns, etc just like you can in the base MythicMobs directory. Inside these folders you can treat it just like the base folders as well putting as many files for the respective type as you want. Easy to zip up and then hand out!

## Pack Info
When making a Pack, you might want to embed a bit more information into it, such as who is the author, the Pack name an so on. This is possible via the creation of a `packinfo.yml` file inside the pack's main directory.

```yaml
Name: The name of the pack
Version: 0.1.0
Author: The name of the author
Icon: the block to use as the icon of the pack
URL: The link to your site, if any
Description:
- This is a list
- of things that will appear
- as the pack's description
- &aYou can also use color codes!&r
```

This will be visible when a user hovers over the pack icon by accessing the MythicMobs menu via the `/mm menu` command and going in any of the available section. If the Pack contains items relevant with the selected section, it will be displayed
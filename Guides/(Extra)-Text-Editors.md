When working with MythicMobs, knowing how everything works is only half the battle: the other half is writing it down, and if you are not using a proper text editor, it might prove challenging to manage all of the files and configurations you will need to make. Fortunately, there are a lot of cool options out there! While in this guide we will be focusing only on [Visual Studio Code](https://code.visualstudio.com/Download) as it is the editor on which the [MythicScribe Extension] can be used, any text editor will work fine!


## [VSCode Extension](https://marketplace.visualstudio.com/items?itemName=Lxlp.mythicscribe)

## Creating a Workspace
One of the most handy features of VSCode is the ability to create a "Workspace", essentially something that will allow you to persistently keep all open files and use custom settings for your project. To make a Workspace, you can start by right clicking the folder you want to start on: for Mythicmobs, this folder can be either the root folder or that of a [Pack](Packs), depending on what you are using and what you want to do  

- You can select a folder by right clicking it and selecting "Open with Code"  
![Selecting a folder](https://i.imgur.com/pOPO9cI.png)
- After you have opened that, you can navigate to `File > Save Workspace As...` and select a valid path for the new workspace file to be created  
![Creating a Workspace](https://imgur.com/2CWpJnK.png)
- To open the workspace again, you can double click on the generated workspace file  
![Workspace file](https://imgur.com/Ja7mZcg.png)

And that's all! You just created a workspace, that will allow you to more easily keep track of changes and edit things!


## Customizing The Workspace
After a workspace has been created, workspace-specific settings can be made, so that only the selected workspace will have them, as to not "mess up" other working areas.  
To access them, after having opened the workspace, you can navigate to `File > Preferences > Settings > Workspace` and set them up!
![Workspace Settings](https://imgur.com/OpWkcEG.png)


## Workspace Utilities
##### Editing Files
- You can both create, edit and rename files and folder directly in Vscode's Explorer: just right click the relevant folder/file and select what you want to do
##### Pinning Tabs
- You can pin important tabs by right clinking then and selecting `Pin`. This will not only keep them open, but using any "close all" option will not close pinned tabs and they will be fixed at the start of the tab list
##### Split View
- In case you need to work both on a skill and mob file at the same time, you can split one of them, so you can see both of them at the same time. For this, simply click on the relevant open tab and select "Split X", where X is the desired location (Up, Down, Left, Right)
##### Bulk Changes
- If you want to rename a metaskill or a mob, you can:
  - Use the search and replace function you can find on the right (the magnifying glass icon) to change that across all workspace files
  - Use the `Change All Occurrences` button (Select the word you want to change and use right click) to change every occurrence of that word inside of its file
- If you need to edit more than one line at the same time, you can click the middle mouse button and drag it over the relevant lines to create a cursor on each on them, and edit them all at the same time


<!-- LINKS -->
[MythicScribe Extension]: https://marketplace.visualstudio.com/items?itemName=Lxlp.mythicscribe
Note: Altium Designer is natively compatible with SVN and CVS. My add-ons are compatible with SVN only because of the use of custom scripts that are developed specifically for SVN. Apart of those ones, everything should be CVS compatible.

# A menu for SVN actions
I created a menu with keyboard shortcuts for built-in SVN operations and call to my custom SVN scripts. If you read on, you will be able to create the same menu to use it in your environment.

![custom SVN menu](https://github.com/Altium-Designer-addons/scripts-libraries/raw/master/Menu_SVN/Menu_SVN.png)

An important thing to understand is that each function can work **only if** you have the **focus** on a document that is able to interact. For example the function "Lock" will only work if it is applied when you are currently working (under focus in Altium Designer) on a file that is under version control.  
Menu items that are greyed out mean they cannot apply on that file. Example: cannot Unlock because the file is not locked, cannot Add because the file is already under version control.

Below is the list of functions and associated shortcuts present in the menu.

|Feature|Keyboard shortcut|Special instructions|
|:---|:---|:---|
|Lock|CTRL + ALT + K|
|Unlock|CTRL + ALT + N|
|Refresh|CTRL + ALT + R|
|TSVN Commit folder|CTRL + ALT + PgUp|Needs [this script](https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/TortoiseSVN) + TortoiseSVN, see the prerequisites below|
|TSVN Update folder|CTRL + ALT + PgDn|Needs [this script](https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/TortoiseSVN) + TortoiseSVN, see the prerequisites below|
|Commit whole project|CTRL + ALT + M|
|Update whole project|CTRL + ALT + U|
|Revert local modifications|CTRL + ALT + V|Not valid with Output Job files ; Needs [this script](https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/BetterRevertVCS), see the prerequisites below|
|Add to version control|CTRL + ALT + I (I like "Insert")|Not valid with Output Job files|
|Remove from version control|CTRL + ALT + D|

**Warning 1**: The functions « Commit whole project » and « Update whole project » apply to the currently active project. If the currently open document is not inside a project, the functions cannot be used.  
**Warning 2**: The functions « TSVN Commit folder » and « TSVN Update folder » apply to the whole content of the directory containing the current file or project. If the current file has never been saved on the disk, the functions cannot be used. Those two functions also need TortoiseSVN to be installed on the computer.



# Create the menu
## Prerequisites
Before the creation of the menu you need to follow those instructions:
1. Create a folder named exactly "AltiumDesigner_AddOns" on your root drive C:\
1. Create two other folders into "C:\AltiumDesigner_AddOns\": "MenuIcons" and "Scripts"
1. Download the content of https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/Menu_SVN/Icons and put it into the directory "C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN"
1. Download the content of https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/BetterRevertVCS and put it into the directory "C:\AltiumDesigner_AddOns\Scripts\BetterRevertVCS"
1. Download the content of https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/TortoiseSVN and put it into the directory "C:\AltiumDesigner_AddOns\Scripts\TortoiseSVN"
1. Install [TortoiseSVN](https://tortoisesvn.net) (free and open source) to get the full potential of the TortoiseSVN script and menu

You should now have the following folder structure:  
> C:\AltiumDesigner_AddOns\

>> MenuIcons
>>> [icon files]

>> Scripts
>>> BetterRevertVCS
>>>> [script files]

>>> TortoiseSVN
>>>> [script files]

## Import the menu
Now that everything is ready:
1. [Download the pre-made preference file](https://github.com/Altium-Designer-addons/scripts-libraries/raw/master/Menu_SVN/DefaultPreferences_with_SVN_menu.DXPPrf) wherever you want on your drive.
1. Open Altium Designer and click DXP > Preferences.
1. Use the bottom button "Import" to select the previously downloaded preference file.
1. Deselect all options but "System > Customizations" like in the screen capture below and click OK.
1. Restart Altium Designer and open a Schematics or PCB file to see the new menu.

![how to import a custom menu](https://github.com/Altium-Designer-addons/scripts-libraries/raw/master/Menu_SVN/Load_Custom_Menus_Altium.png)

## Before use
All menus in Altium Designer are "contextual", i.e. depend on the file being edited. For this reason, the proposed menu and shortcuts are only available in the following contexts:
- Schematics editor (for example with a *.SchDoc file)
- PCB editor (for example with a *.PcbDoc)
- Symbol library editor (for example with a *.SchLib file)
- Footprint library editor (for example with a *.PcbLib file)
- Output Jobs (for example with a *.OutJob file)

To have the functions usable more widely you need to create a new menu manually in each new context.



# Appendix: Manual creation of your own menu
Instead of importing a configuration file you can do it the hard way by re-creating the menu yourself. Use "DXP > Customize" or right-click on any menu item and choose "Customize". Use the information below to fill in the menu creation forms.  
To have the icons shown correctly you need to follow the instructions from the section "prerequisites" above.

[Read the instructions](https://github.com/Altium-Designer-addons/scripts-libraries/blob/master/Menu_SVN/AltiumDesigner_SVN_menu_configuration.txt)

Do not forget that you probably need to create the same menu many times if you want it to be accessible in several contexts (e.g. Schematic editor, PCB editor, SCH library editor, etc.). If you do not have specific needs you are encouraged to import the preference file.
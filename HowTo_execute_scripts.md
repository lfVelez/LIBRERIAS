# Introduction #

In this tutorial, we would try to guide you through the process of executing scripts in Altium Designer.
There are 3 ways of doing this:
  1. The "Run script" command
  1. A custom menu item
  1. A custom toolbar

For advanced information about scripting in Altium Designer, please refer to [the official documentation](http://techdocs.altium.com/display/SCRT/Scripting).


# Understanding Altium script files #

There are three types of files used by Altium Designer in the scripting system:
  * The script project file (`*.PrjScr`). It works as any other project files: it "groups" files together. You can define some options for the project.
  * The script "unit". It contains some programming code in one of the recognized languages (accepted languages are listed on [the Altium documentation page](http://techdocs.altium.com/display/SCRT/Scripting)).
  * The script "form". If your script has graphical capabilities, it probably has a "form" file having the same name as the "unit": this is the definition for a window.


# Solution 1: "Run script" #

From the "DXP" menu, click on "Run script" in the right column.
A new window appears showing a list of available script, that is:
  * Scripts made globally available in the preferences (DXP > Preferences > Scripting system > Global projects). This requires to have a project script file (`*.PrjScr`).
  * Scripts available in the Projects panel, either because they are part of a project or because they are open as free documents.

The list is actually a tree of this form:
  * Script project (`*.PrjScr` or Free documents)
    * Script file (accepted languages are listed on [the Altium documentation page](http://techdocs.altium.com/display/SCRT/Scripting))
      * Function inside the script (if any)

Choose either a script file or a particular function and click "OK" to run it.

_The script itself is visible but some functions are missing in the list ? Do these functions require some input parameters? Well, the "Run script" dialog is not able to let you start this type of functions because you cannot input anything from there, sorry._


# Solution 2: New menu item #

Want to have access to a script by a menu entry?

You have two possible starting points:
  * DXP > Customize
  * Right-click on an existing menu > Customize

Then in the section `[Scripts]` you get a list similar to the one from "DXP > Run script". Drag and drop the requested script file or function in the menu bar, then customize the menu entry with a name, description, image, shortcuts, etc.
When you have closed the "Customize" dialog, your menu entry becomes fully functional and must launch your script properly.


# Solution 3: New toolbar #

If you prefer to not put your dedicated script launchers inside the main menu, you can create your own toolbar:
  1. DXP > Customize
  1. Switch to the "Toolbars" tab
  1. Click on "New", give your toolbar a name

Now that you can find your new (but empty) toolbar in the Altium Designer interface, you can follow the steps of Solution 2 to add a link to a script.

_Cannot locate your freshly created toolbar? Disable then re-enable it, you would probably see it as a "flash" appearing between existing menus._


# In video #

Thanks to Petar PERISIN, you will be able to see most of the points covered in this tutorial in a [single and short video](https://www.youtube.com/watch?v=w62Hg0EqTVs).
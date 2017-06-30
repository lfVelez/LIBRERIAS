# A menu for SVN actions
I created a menu with keyboard shortcuts for built-in SVN operations and call to my custom SVN scripts.

![custom SVN menu](https://github.com/Altium-Designer-addons/scripts-libraries/raw/master/TortoiseSVN/Menu_SVN.png)

Here is the list of custom shortcuts which I added to Altium Designer:

|Feature|Shortcut|Special instructions|
|:---|:---|:---|
|Lock|CTRL + ALT + K|
|Unlock|CTRL + ALT + N|
|Refresh|CTRL + ALT + R|
|TSVN Commit folder (using TortoiseSVN)|CTRL + ALT + PgUp|Needs a [custom script](https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/TortoiseSVN) + TortoiseSVN, see the pre-requisites below|
|TSVN Update folder (using TortoiseSVN)|CTRL + ALT + PgDn|Needs a [custom script](https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/TortoiseSVN) + TortoiseSVN, see the pre-requisites below|
|Commit whole project|CTRL + ALT + M|
|Update whole project|CTRL + ALT + U|
|Revert local modifications|CTRL + ALT + V|Not valid with Output Job files ; Needs a [custom script](https://github.com/Altium-Designer-addons/scripts-libraries/tree/master/BetterRevertVCS), see the pre-requisites below|
|Add to version control (Insert)|CTRL + ALT + I|Not valid with Output Job files|
|Remove from version control (Delete)|CTRL + ALT + D|

**Warning 1**: The functions « Commit whole project » and « Update whole project » apply to the currently active project. If the currently open document is not inside a project, the functions cannot be used.  
**Warning 2**: The functions « TSVN Commit folder » and « TSVN Update folder » apply to the whole content of the directory containing the current file or project. If the current file has never been saved on the disk, the functions cannot be used. Those two functions also need TortoiseSVN to be installed on the computer.



# Create the menu
All menus in Altium Designer are "contextual", i.e. depend on the file being edited. For this reason, the menu and  shortcuts are available in the following contexts:
- Schematics editor (for example with a *.SchDoc file)
- PCB editor (for example with a *.PcbDoc)
- Symbol library editor (for example with a *.SchLib file)
- Footprint library editor (for example with a *.PcbLib file)
- Output Jobs (for example with a *.OutJob file)
## Pre-requisites
To be written
-> paths
## import
-> file!
## create manually
-> appendix



# Appendix: SVN menu configuration

SV&N  
N

> VersionControl:VersionControl  
ObjectKind=FocusedDocument|Action=Lock  
Loc&k  
Lock active document  
C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Lock.bmp  
Alt + Ctrl + K  

> VersionControl:VersionControl  
ObjectKind=FocusedDocument|Action=Unlock  
U&nlock  
Unlock active document  
C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Unlock.bmp  
Alt + Ctrl + N  

> VersionControl:VersionControl  
ObjectKind=FocusedProject|Action=RefreshProject  
&Refresh  
Refresh status from version control repository  
C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Refresh.bmp  
Alt + Ctrl + R  

> ScriptingSystem:RunScript  
ProjectName=C:\AltiumDesigner_AddOns\Scripts\TortoiseSVN\TortoiseSVN.PrjScr|ProcName=C:\AltiumDesigner_AddOns\Scripts\TortoiseSVN\TortoiseSVN.vbs>TSVN_CommitFolder  
TSVN &Commit folder  
Commit the whole folder with TortoiseSVN  
C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\TSVN_Commit.bmp  
Alt + Ctrl + PgUp  

> ScriptingSystem:RunScript  
ProjectName=C:\AltiumDesigner_AddOns\Scripts\TortoiseSVN\TortoiseSVN.PrjScr|ProcName=C:\AltiumDesigner_AddOns\Scripts\TortoiseSVN\TortoiseSVN.vbs>TSVN_UpdateFolder  
TSVN &Update folder  
Update the whole folder with TortoiseSVN  
C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\TSVN_Update.bmp  
Alt + Ctrl + PgDn  

> &Advanced functions

>> VersionControl:VersionControl  
  ObjectKind=FocusedProject|Action=CommitProject  
  Co&mmit whole project  
  Commit project documents to version control  
  C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Commit.bmp  
  Alt + Ctrl + M  
  
>>  VersionControl:VersionControl  
  ObjectKind=FocusedProject|Action=UpdateProject  
  &Update whole project  
  Update project documents from version control  
  C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Update.bmp  
  Alt + Ctrl + U  
  
>>  ScriptingSystem:RunScript  
  ProjectName=C:\AltiumDesigner_AddOns\Scripts\BetterRevertVCS\BetterRevertVCS.PrjScr|ProcName=C:\AltiumDesigner_AddOns\Scripts\BetterRevertVCS\BetterRevertVCS.vbs>BetterRevertVCS  
  Re&vert local modifications  
  Revert local modifications to focused document  
  C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Revert.bmp  
  Alt + Ctrl + V  
  
>>  VersionControl:VersionControl  
  ObjectKind=FocusedDocument|Action=Add  
  &Add to version control  
  Add focused document to version control  
  C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Add.bmp  
  Alt + Ctrl + I  

>>  VersionControl:VersionControl  
  ObjectKind=FocusedDocument|Action=Remove  
  &Remove from version control  
  Remove focused document from version control  
  C:\AltiumDesigner_AddOns\MenuIcons\Menu_SVN\Delete.bmp  
  Alt + Ctrl + D  
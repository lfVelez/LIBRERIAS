[Download here](https://drive.google.com/file/d/0B9wYgjewDMDFTko4WTdzaVBGLUE/edit?usp=sharing)

**If you have some other net tie components or other components which you want to share on Altium Addons page, please let us know via email retry.var (a) gmail.com.**

The library NetTieLib is distributed "as is" with no warranty. The library contains special Net Tie components which are used in Altium Designer to split one signal/net into several signals/nets or join several signals/nets into one signal/net. The Net Tie component is in fact creates short circuit connection of the signals. Altium Designer do not reports those short circuit connections as DRC violation if the connection is done by the cooper parts of the Net tie component.
The library was created as a template. Please feel free to modify the library components according to your design standards.

The library is distributed free of charge.

# Package content #
  * **[NetTieLib.IntLib](NetTieLib#List_of_library_components.md)** - integrated library NetTieLib which can be installed and used in Altium Designer
  * **Documentation\** - documentation to NetTieLib and Net Tie components in general
  * **[DRC exceptions\](NetTieLib#Design_Rule_Check_exceptions.md)** - RUL files with DRC exception rules which suppress violations in PcbDoc when NetTieLib components are used
  * **[NetTieLibSampleBoard\](NetTieLib#Sample_Board.md)** - sample PCB project with all components from the NetTieLib, DRC exception rules applied
  * **NetTieLibSource\** - source files used for building NetTieLib.IntLib, you can open NetTieLib.LibPkg file in Altium Designer,  modify the library and compile it back into IntLib file which will be located in NetTieLibSource\Outpupt\



# Net Tie component? #
Special kind of component in Altium Designer which aims to join or split signals in particular point on board. This can be done on a layer (mos of components in NetTieLib) or by via on different layers (NetTieVia component).
Detailed description of Net Tie component type can be found in Documentation\NetTies-and-How-to-Use-Them.pdf in the Libs\_NetTieLib package.


# Library design parameters #
The library design parameters were set by need of regular low and medium density boards. Footprints should be modified accordingly to comply with your design standards or needs - different clearance, smaller/bigger footprints, microvias, burried/blind vias etc.

Clearance 0.2mm = distance of pads including attached track ends to other pads with their trackends
## Footprint variants by suffix ##
  * LP = Low Power - for track width up to 12mil/0.3mm ~ max. 1A@(Cu 18um, temp rise 10°C)
  * MP = Medium Power - for track width up to 40mil/1mm ~ max. 2.5A@(Cu 18um, temp rise 10°C)
  * HP = High Power - for track width up to 120mil/3mm ~ max. 5A@(Cu 18um, temp rise 10°C)
Net tie vias LP, MP, HP are through hole vias with hole 0.3, 0.6 and 0.8mm and outer diameter 0.6, 1.0 and 1.4mm.

# Design Rule Check exceptions #
Net Tie components produce some of DRC violations. These violation should be addressed by additional rules - exceptions - from the standard technology. The rule exceptions are prepared in folder _DRC exceptions_ in NetTieLib package. There are 3 files included, please use/modify those rules in context of your design.
  * **NetTieViasHoleToHole.RUL** - rule necessary for suppressing HoleToHole violation when NetTieVia component is used. Routing of these components is usually done in Ignore Obstacles routing mode. All pads of the NetTieVias must be added to Pad Class with name NetTieVias unde Design >> Classes.

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieViasPadClass.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieViasPadClass.png)

  * **GNDtopologyStar.RUL** - rule defines StarPoint component as a center of starburst routing topology in GND net
  * **NetTieComponentClearance.RUL** - rule which removes 3D component clearance check to NetTieLib components (excluding Solder junctions) what allows to have them under other components
The rules can be imported in PCB editor by menu Design >> Rules and righ mouse click on Design Rules item in the tree list and selecting Import Rules

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/RULimport.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/RULimport.png)


# List of library components #
| Name | Symbol(s) | Footprint (MP version only) | Description | Note |
|:-----|:----------|:----------------------------|:------------|:-----|
| 2way | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2wayPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2wayPCB.png) | 2 way net tie junction | Typically used for joining two nets together, e.g. AGND and DGND |
| 3wayT | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayTSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayTSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayTPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayTPCB.png) | 3 way net tie junction T shape | Typically used for splitting signal to two receivers on board, e.g. clock signal to 2 ICs  |
| 3wayY | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayYSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayYSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayYPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3wayYPCB.png) | 3 way net tie junction Y shape |      |
| 4way | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/4wayCrossSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/4wayCrossSch.png)![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/4wayHSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/4wayHSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/4wayPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/4wayPCB.png) | 4 way net tie junction | Schematic symbol has alternative graphics, see component Properties >> Display mode in schematic editor. |
| NetTieVia | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieViaSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieViaSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieViaPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieViaPCB.png) | Net Tie Via | Connected signals are usually spread on different layers. Ignore Obsatacles routing mode should be used. |
| StarPoint | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/StarPointSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/StarPointSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/StarPointPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/StarPointPCB.png) | Star point for definition of starburst topology | Routing topology rule must be applied in PCB. The rule can be imported from GNDtopologyStar.RUL, see [Design Rule Check exceptions](NetTieLib#Design_Rule_Check_exceptions.md) section. |
| 2waySolderNC | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNCSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNCSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNCPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNCPCB.png) | 2 way net solder junction - Normally Connected | Soldered connection marked in silkscreen and by 3D body. |
| 2waySolderNO | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNOSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNOSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNOPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolderNOPCB.png) | 2 way net solder junction - Normally Open |      |
| 3waySolder | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3waySolderSch.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3waySolderSch.png) | ![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3waySolderPCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3waySolderPCB.png) | 3 way net solder junction | Soldered connection marked in silkscreen and by 3D body. |

# Sample Board #
All NetTieLib components on one schematic. Blankets (yellow polygons) are used for definition of net classes for LP, MP and HP sections and for definition of track width in the end.

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieLibSampleSchematic2.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieLibSampleSchematic2.png)

Sample board with all NetTieLib components.

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieLibSamplePCB.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieLibSamplePCB.png)

3D view of 2 way solder junctions Normally Closed (NC) and Normally Open (NO) version displayed. Soldered connection marked in silkscreen and by 3D body.

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolder3D.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/2waySolder3D.png)

3D view of 2 way solder junction. Soldered connection marked in silkscreen and by 3D body.

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3waySolder3D.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/3waySolder3D.png)

NetTieVias example in 2D view. Every track is in different net and is placed on separated layer.

![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieVias2D.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieVias2D.png)
![https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieVias3D.png](https://raw.githubusercontent.com/Altium-Designer-addons/scripts-libraries/master/%23Libraries/Libs_NetTieLib/Documentation/wiki/NetTieVias3D.png)

# Rhino-Tools
![Rhino](https://github.com/Makersmic/Rhino-3d-Printer/edit/main/Tools/Readme.md)
The Rhino Motion System utilizes replaceable tools mounted to the x axis motion carriage.  Tools 'slot' into place and auto-align from the v-groove style slot found on the front of the carriage.  The tool is further held in place by an m3x50mm bolt and knurled nut(or wingnut) combination.  Tools currently available are:

The Jack Rabbit 24v 3d printing tool head 

12v 40w Blue Diode Laser Cutting tool head

24v Spindle with ER8 Collet


Development underway for a needle cutter tool head and Roland Drag Knife toolset.

Implementation of all of the tools is conducted through what is affectionately called the Umbilical and the Hub.  

The Umbilical, through the use of a male/female 21w4 dsub connector is able to effectively provide connection points for all of the tools listed above.  Mating point is at the top rear frame with the Hub directly below.  With the mating point located in the rear it allows the tool to only carry wiring specific to that tool.  Constant hardware connections such as endstops are not part of Umbilical.

insert image here

The Hub is effectively a series of wago style terminal blocks providing quick and easy connections points to the Umbilical, control boards, and other related hardware.

insert image here

To change the Rhino from 3d printer mode to laser/spindle/drag knife mode a user needs to uncomment the line stating include [3dp.cfg].  This will disable things like thermistors and related 3d printer expections from the firmware parameters.










![Rhino](https://github.com/Makersmic/Rhino-3d-Printer/blob/main/Literature/4A271D9A-36F3-4DF0-B862-CE5E58B66D81.jpeg)

# Tools:
The Rhino Motion System utilizes replaceable tools mounted to the x axis motion carriage.  Tools 'slot' into place and auto-align from the v-groove style slot found on the front of the carriage.  The tool is further held in place by an m3x50mm bolt and knurled nut(or wingnut) combination.

Tools currently available are:

-The Jack Rabbit 24v Volcano 3d printing tool head 

-12v 40w Blue Diode Laser Cutting tool head

-24v Spindle with ER8 Collet

-Development underway for a needle cutter tool head and Roland Drag Knife toolset.

Implementation of all of the tools is conducted through what is affectionately called the Umbilical and the Hub.  

## The Umbilical
Through the use of a male/female 21w4 dsub connector is able to effectively provide connection points for all of the tools listed above.  Mating point is at the top rear frame with the Hub directly below.  With the mating point located in the rear it allows the tool to only carry wiring specific to that tool.  Constant hardware connections such as endstops are not part of Umbilical. 

Constant connections include:

-3 wires for endstop

-2 20mm soft tube aire connections

-2 wire chamber thermistor

-2 wire led strip.



*Note-the Backbone of the Umbilical provides for multiple configurations if a user desires to use hardware not covered within this documentation.


insert image here

## The Hub
Effectively a series of wago style terminal blocks providing quick and easy connections points to the Umbilical, control boards, and other related hardware inside of the control panel area.

insert image here

## Tool Swap

To change the Rhino from 3d printer mode to laser/spindle/drag knife mode a user simply needs to mount the appropriate tool ensuring the Umbilical is fully seated at the mounting point and then use appropriate programs for gcode generation.  Currently there is not a self-check in place for gcode to match the appropriate tool.

*Note: When using the Rhino for functions outside of 3d printing and while navigating the online interface of Fluidd or Mainsail, 3d printer nozzle temp is general temperature of the tool.








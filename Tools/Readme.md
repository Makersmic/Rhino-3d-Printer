

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


<img src="https://github.com/Makersmic/Rhino-3d-Printer/blob/main/Electrical/Images/JQX-13FL.jpg" width="250" height="200">

## The Hub
Effectively a series of wago style terminal blocks providing quick and easy connections points to the Umbilical, control boards, and other related hardware inside of the control panel area.

insert image here

## Tool Swap

To change the Rhino from 3d printer mode to laser/spindle/drag knife mode a user simply needs to mount the appropriate tool ensuring the Umbilical is fully seated at the mounting point and then use appropriate programs for gcode generation.  Currently there is not a self-check in place for gcode to match the appropriate tool.

## How does this all work together?
All of the tool modules utilize a 21w4 male connector whilst connecting to a 21w4 female connector located at the rear of the Rhino.  A couple things to keep to get this all to work.  Klipper needs various inputs due to their specification in the firmware, mainly thermistor sensors providing input if specified.  Some have pondered as well as myself for quite some time how do get around this when switching tools that don't require those inputs and through time the answer became clear.  While some of the tools themselves may not require a temp reading, that doesn't mean we can't provide one.  An example of this would be the 3d printing module vs the laser module, when 3d printing Klipper requires a temp reading from the hotend, but if we switch that tool over to the laser module we still need to provide that temp reading that Klipper is looking for.  Simple, just add a thermistor to the laser tool.  What i chose to do is mount a thermistor to the heatsink portion of the laser module keeping in mind that i needed to use the same type of thermistor that was used on 3d printing tool.  Because I've chosen this method i no longer need to go my printer.cfg file and uncomment/comment out things for the laser module to work.








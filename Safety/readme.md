# Safety
## Introduction
When people in the 3d printing talk about saftey there seems to be a universal concern, fire.  In terms of the Rhino though i wanted to expand this subject out more due to the 
multiple tools that can be utilized and the change procedures revolving around those tools.  

To address fire safety i want to install smoke alarms with relays.  The purpose of the smoke alarm having a relay is that the relay can be tied into the endstop inputs of the control 
board, thus making Rhino aware of when smoke/fire occurs and further more enabling Rhino to take action.

### Smoke Detection Module:
MQ-2.....Aliexpress $10

This smoke detector can operate on 12v or 24v and is small in size,49x45x20mm

Currently there is an excess of endstop inputs available, with 3 available on the m5 and 5 available on the gtr.

In addition to the smoke detection modules, the printer must have 110v and 220v relays that are tied into the power supplies of the printer.  Without these killing power to the
control board or other components will not be possible.  It may also be needed to run secondary mcu to support fire protocols when the printer has been powered off.  To
take a step further i can even see this secondary mcu having it's own power source that is not tied into mains power but rathe run from a rechargeable battery pack that is constantly
charged.  Utilizing 18650 batteries in a battery pack of some kind could be an avenue traveled for this aspect.

## Anticipated zones for smoke and fire:
-Build Chamber-This sensor will be located in the lid.

-Control Cabinet-These sensors one on each side will be mounted on the same din rails as the other components.  One for each side so a total of 2 sensors, will be mounted in the middle of top
din rail.

-Build Plate-Rhino utilizes 'air gap' insulation for the heated build plate.  The open pocket of air between the silicone heated mats and the cover located on the bottom side of the plate there is clearance to be able to install a smoke detector.

-Power Supply/Power Distribution Area-This sensor would be located in the area within close proximity to the power supplies and the bank of terminal blocks acting as power 
distribution.

## Actions
The macro that is written needs to do a couple things to ensure the long life of our printer:
-Immediately or almost immediately killing power to the 3d printer.

-Storing the last position of the print head much like that of when the printer is paused.

-Informing the user that smoke has been detected though the main display, or possibly tying it into telegram bot so a user can get messages sent directly to a device that they keep on their person.


In retrospect, all of the actions described above will come with conditions, or perhaps not triggered until a requirement is met or not met.


This subject needs to be expanded upon.

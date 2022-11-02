## Hardware Overview
Everyone knows the old saying, 'There's more than one way to skin a cat.'  It's gross, but it's true.  The following hardware listed below is what I am currently using.  The posted firmware configuration files will follow this hardware.

### Klipper MCU
Rpi 3+

### Mainboard
SKR GTR with the accompanying M5 board

In no particular order the reasons for choosing this board were that while the GTR can be supplied 24v, the M5 can be supplied 12v.  This especially handy when having to control devices that are 24v and 12v.  A quick shoutout would be having 24v 3d printing hardware but then also having a 12v laser module in the arsenal.  Another reason I chose this combination is that the M5 connects directly to the GTR board so in essence I'm saving a usb port on the Rpi.  Lastly, the GTR has a good amount of inputs and output but with the addition of the M5 it gives the Rhino an over-abundance of possiblities for future tool modules.

### Power
24v power supply

12v power supply

5v power supply

### Relays
I chose to use din mount style relays for the reason of ease of use, if one was to become faulty and needed replacement or if one needed to be upgraded this could easily be achieved.  While some of the relays seem rather hefty, I wanted to leave plenty of headroom for future hardware not yet concieved.  You will see this also when studying the control panel layout and notice the gage of some wire used for the runs.  The other reason choosing to use relays was to isolate the board from heavy loads that could potentially cause the board to overheat.

With the exception of the ssr's used for the heated bed mats i chose to use mechanical relays.  I find it easier to troubleshoot this style and the audible click is re-assuring to hear when a device is kicked on.

#### 12v low amperage circuits: *led lighting, neopixel lighting, fans, etc*
700-TBR24 6A relay

#### 12v high amperage circuits: *laser module, vacuum pump*
JQX-13FL 10A relay

#### 24v high high amperage circuits: *spindle module*
JQX-38F 40A relay
![JQX-38F](https://github.com/Makersmic/Rhino-3d-Printer/Electrical/Images/JQX-38F.jpg)

### Distribution Blocks
I chose two different styles depending on the application.  

#### Umbilical Interface
Wago Style that does not have the ability to be bridged

#### Power Distribution
Traditional distribution blocks that have the ability to be bridged


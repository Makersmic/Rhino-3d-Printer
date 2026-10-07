The following settings and gcode are geared towards Laserweb 4.0.  While the following may work for previous versions or in fact other software, it has not been tested otherwise.  

To setup Laserweb perform the following:
1.  Click on Settings
2.  Click on Gcode
3.  Ensure the following is in the "Gcode Start" section:
      home        ; Rhino default homing sequence
      G1 F1000    ; Set the feedrate
      G21         ; Set units to mm
      G90         ; Absolute positioning
      M106 S230   ; Set the part cooling fan to 75%
      SET_PIN PIN=VACPUMP_pin VALUE=1   ;Power on the laser module
      
4.  Ensure the following is in the "Gcode End" section:
      G1 Z220 F1000     ;Lower the build plate
      M106 S0           ;Turn off the part cooling fan
      SET_PIN PIN=VACPUMP_pin VALUE=0   ;Power off the laser module
      
5.  Ensure the following is in the "Tool Off Section":
      SET_PIN PIN=LASERPOWER_pin VALUE=0  ;Set the laser pwm signal to '0'.

6.  Ensure the following is in the "Laser Intensity" section;
      SET_PIN PIN=LASERPOWER_pin VALUE=
      
7.  Ensure that '0' is in the "PWM MIN S VALUE" field.

8.  Ensure that '1' is in the "PWM MAX S VALUE" field.

9.  "Gcode Homing" and "Tool On" sections are to be left blank intentionally.

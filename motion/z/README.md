## Z-Axis
The z-axis of the Rhino utilizes a triple leadscrews with kinematic couplings attaching the buildplate.  The rear leadscrew is T12x2 with 3:1 gear ratio using a 60 tooth 2gt pulley and 20 tooth 2gt pulley.  The front leadscrews are T8x2 with a 3:1 gear ratio as well utilizing 30 tooth 2gt pulleys and 10 tooth 2gt pulleys.  All pulleys are designed for closed loop 2gt 15mm belts accomodating 180-190mm loop size. 


> **Klipper setting:** `printer.cfg` uses `gear_ratio: 2:1` on all three Z steppers - the value that measures correctly on the machine. The pulley counts above are being re-checked against it.

Because each corner has its own motor, Klipper trams the bed with `Z_TILT_ADJUST`. Parts are in [leadscrew-based](leadscrew-based/).

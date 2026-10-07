# Z axis

The bed rides on **three leadscrews** joined to the build plate by kinematic couplings: one **T12×2** at the rear and
two **T8×2** at the front. Each screw has its own stepper and is belt-driven through a **2:1 reduction** on closed-loop
2GT 15 mm belts (180–190 mm loop).

Klipper matches this with `gear_ratio: 2:1` on all three Z steppers (`stepper_z`, `stepper_z1`, `stepper_z2` in
`printer.cfg`). Because each corner has its own motor, Klipper trams the bed with `Z_TILT_ADJUST`.

Parts are in [leadscrew-based](leadscrew-based/).

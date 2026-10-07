# HotJoe

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="images/hotjoe-dark.png"><img src="images/hotjoe-light.png" alt="hotjoe" height="320"></picture></p>

**CNC spindle - light engraving and milling** · slot 4 in the Tool Manager

A brushless motor (2814, 1000 kV) with an ER8 collet, driven by an 80 A HobbyWing ESC on 24 V. A 40 A relay
powers the ESC only while the spindle is in use; the speed signal runs at 400 Hz. Intended for light-duty work -
check real speeds at the collet with a tachometer before relying on them, and calibrate the ESC once with
`CALIBRATE_ESC`.

## Files

| File | What it is |
|---|---|
| `Spindle Assembly.step` | Complete spindle assembly |
| `Spindle Main Body.step`, `Main Body Mount Clip v2.step`, `Spindle Carriage Mount Clip.step` | Body and carriage mounting |
| `Tensioner Body.step`, `Tension Arm Shield.stl` | Belt drive tensioner |
| `Motor Shield.step`, `Gearbox Shield.step` | Safety covers |
| `70mm cnc brush holder.step` | Brush skirt for dust collection |
| `Blow Air Clip v1.step`, `turbine.stl` | Blow-air nozzle |

## Tool connector (21W4)

Contacts this tool uses. Pins 1, 2, 11 and 12 are the high-current contacts. Full wiring: [electrical](../../electrical/).

| Contact | Use |
|---|---|
| 3 | Thermistor |
| 4 | Thermistor |
| 11 | 24 V relay power |
| 12 | 24 V relay power |
| 13 | Probe |
| 14 | Probe |
| 15 | Probe |
| 18 | PWM |

## Running it

- **Set up a job with:** `CNC_JOB_SETUP FILE=<name>.gcode`
- **Outputs in Klipper:** Spindle_power relay, SPINDLE_SPEED ESC signal
- **Macros:** `CNC_JOB_SETUP`, `SET_WORK_ZERO`, `PROBE_Z_WORK_ZERO`, `G54`, `Spindle_ACTIVATE`, `Spindle_DEACTIVATE`, `CALIBRATE_ESC`

Config, macros and the Tool Manager portal live in **[Toolhead_Manager](https://github.com/Makersmic/Toolhead_Manager)**; the user manual there has a full chapter on each tool.

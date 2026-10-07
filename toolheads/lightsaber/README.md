# LightSaber

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="images/lightsaber-dark.png"><img src="images/lightsaber-light.png" alt="lightsaber" height="320"></picture></p>

**Laser cutting and engraving** · slot 3 in the Tool Manager

A 12 V blue diode laser for cutting vector shapes from flat sheet and engraving. A relay switches its 12 V
supply (contacts 20-21) and Klipper drives its intensity (contacts 16-17). A thermistor on the heatsink keeps Klipper
happy and lets the swap wizard confirm the umbilical is seated. The printed **height gauge** sets the focus distance.

**Safety:** wear glasses rated for the laser's wavelength, run extraction, never cut PVC or vinyl, and stay with the
machine for the whole cut.

## Files

| File | What it is |
|---|---|
| `Laser Mount.step` | Mount that slots onto the X-carriage |
| `Height Gage.step` | Printed gauge for setting focus height |

## Tool connector (21W4)

Contacts this tool uses. Pins 1, 2, 11 and 12 are the high-current contacts. Full wiring: [electrical](../../electrical/).

| Contact | Use |
|---|---|
| 3 | Thermistor |
| 4 | Thermistor |
| 13 | Probe |
| 14 | Probe |
| 15 | Probe |
| 16 | Laser PWM (5 V) |
| 20 | + 12 V power activate |
| 21 | - 12 V power activate |

## Running it

- **Set up a job with:** `LASER_JOB_SETUP FILE=<name>.gcode`
- **Outputs in Klipper:** LASER_INITIALIZE 12 V rail, SERVO_LASER intensity
- **Macros:** `LASER_JOB_SETUP`, `LASERHOME`, `LASER_FOCUS_ALIGN`, `SET_LASER_POWER`, `ACTIVATE_LASER`, `DEACTIVATE_LASER`

Config, macros and the Tool Manager portal live in **[Toolhead_Manager](https://github.com/Makersmic/Toolhead_Manager)**; the user manual there has a full chapter on each tool.

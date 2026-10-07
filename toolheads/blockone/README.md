# BlockOne

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="images/blockone-dark.png"><img src="images/blockone-light.png" alt="blockone" height="320"></picture></p>

**3D printing - single extruder** · slot 1 in the Tool Manager

BlockOne is the Rhino's single-extruder print head and the updated version of the
[Jack Rabbit](../jack-rabbit/). It uses an E3D v6 Volcano hotend at 24 V with a BMG drive gear for 1.75 mm filament,
with OrcaSlicer profiles for 0.4 mm and 0.8 mm nozzles. Part cooling comes from the Rhino's universal blow-air system.

## Files

> **Build files coming soon.** This folder is ready for BlockOne's STEP/STL files and drawings - upload them here.
> Until then, the [Jack Rabbit](../jack-rabbit/) files show the earlier design.

## Tool connector (21W4)

Contacts this tool uses. Pins 1, 2, 11 and 12 are the high-current contacts. Full wiring: [electrical](../../electrical/).

| Contact | Use |
|---|---|
| 1 | 24 V hotend |
| 2 | 24 V hotend |
| 3 | Thermistor |
| 4 | Thermistor |
| 5 | 24 V hotend fan |
| 6 | 24 V hotend fan |
| 7 | Stepper |
| 8 | Stepper |
| 9 | Stepper |
| 10 | Stepper |
| 13 | Probe |
| 14 | Probe |
| 15 | Probe |

## Running it

- **Set up a job with:** `Slicer start G-code (START_JOB)`
- **Outputs in Klipper:** Hotend heater, hotend fan, part-cooling fan
- **Macros:** `NOZZLE_HEIGHT_CALIBRATE`, `PRIME_LINE`, `PURGE`, `FILAMENT_CHANGE`, `CALCULATE_PA`

Config, macros and the Tool Manager portal live in **[Toolhead_Manager](https://github.com/Makersmic/Toolhead_Manager)**; the user manual there has a full chapter on each tool.

# SwitchFly

<p align="center"><picture><source media="(prefers-color-scheme: dark)" srcset="images/switchfly-dark.png"><img src="images/switchfly-light.png" alt="switchfly" height="320"></picture></p>

**Dual-extrusion 3D printing - one stepper, one nozzle** · slot 2 in the Tool Manager

A direct-drive extruder that feeds two filaments through one stepper motor and one hotend, so there is no
second nozzle to align: no alignment templates or offsets. A servo on the shared `SERVO_LASER` output switches the
filament path (`SWITCH_T0` / `SWITCH_T1`). Built around the E3D v6 Volcano and BMG drive gear, 24 V, 1.75 mm filament.

## Files

> **Build files coming soon.**

## Tool connector (21W4)

Contacts this tool uses. Pins 1, 2, 11 and 12 are the high-current contacts. Full wiring: [electrical](../../electrical/).

| Contact | Use |
|---|---|
| 1 | 24 V + hotend |
| 2 | 24 V hotend |
| 3 | Thermistor |
| 4 | Thermistor |
| 5 | 24 V hotend fan |
| 6 | 24 V hotend fan |
| 7 | Stepper |
| 8 | Stepper |
| 9 | Stepper |
| 10 | Stepper |
| 11 | 24 V + power activate |
| 12 | 24 V - power activate |
| 13 | Probe |
| 14 | Probe |
| 15 | Probe |
| 18 | PWM - signal |

## Running it

- **Set up a job with:** `Slicer start G-code (START_JOB)`
- **Outputs in Klipper:** Hotend heater, fans, filament-path servo (SERVO_LASER)
- **Macros:** `NOZZLE_HEIGHT_CALIBRATE`, `PRIME_LINE`, `PURGE`, `SWITCH_T0`, `SWITCH_T1`, `FILAMENT_CHANGE`, `CALCULATE_PA`

Config, macros and the Tool Manager portal live in **[Toolhead_Manager](https://github.com/Makersmic/Toolhead_Manager)**; the user manual there has a full chapter on each tool.

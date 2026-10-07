# Software

I use free applications wherever possible - licence fees limit development and hurt community growth.

| Job | Software | Notes |
|---|---|---|
| Firmware and control | **Klipper + Moonraker + Mainsail** | Config, macros and the Tool Manager portal are in [Toolhead_Manager](https://github.com/Makersmic/Toolhead_Manager) |
| 3D printing (BlockOne, SwitchFly) | **OrcaSlicer** | Ready-made BlockOne profiles: [`slicer/orca`](https://github.com/Makersmic/Toolhead_Manager/tree/main/slicer/orca). The start G-code calls `START_JOB TOOLHEAD=BlockOne ...` |
| Laser, drag knife, CNC | **Kiri:Moto** (planned) | Free, open-source, browser-based; covers laser, drag knife and CNC in one interface |
| Laser (2023 workflow) | LaserWeb 4 | Old setup notes kept in [archive/2023-apps](../archive/2023-apps/laserweb-setup.md) |

Laser, spindle and drag-knife jobs are started with `LASER_JOB_SETUP`, `CNC_JOB_SETUP` or `DRAGKNIFE_JOB_SETUP`
`FILE=<name>.gcode`, which check the mounted tool and walk through zeroing before the file runs.

## Other useful software

- [Inkscape](https://inkscape.org/) - vector artwork for laser and knife
- [Tinkercad](https://www.tinkercad.com/) - quick 3D models
- [Zamzar](https://www.zamzar.com/) - file conversion

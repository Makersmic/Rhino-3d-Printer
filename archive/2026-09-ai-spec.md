📂 MASTER SPECIFICATION: THE RHINO MULTI-TOOL ECOSYSTEM
🤖 System Introduction & Context
This file serves as the definitive architecture manual and "State of the Machine" baseline for The Rhino—a heavily customized, modular 5-axis hybrid manufacturing workspace powered by Klipper, Moonraker, and an OrcaSlicer frontend. This machine utilizes a shared coordinate rail system but completely switches disciplines based on the physically attached toolhead via a manual, hot-swappable 21-pin umbilical connection line.
🗺️ Stored Global Mappings (variables.cfg)
All macros are explicitly aligned to a single, persistent disk cache file (variables.cfg) via Klipper’s [save_variables] module to prevent volatile dual-tracking sync lag across machine boots:
• Tool Registries: Stored inside a dictionary variable named tool_mapping mapping indexes (0 to 4) to names (BlockOne, SwitchFly, LightSaber, HotJoe, DragKnife).
• Active Hardware Position Tracker: The wizard uses printer["gcode_macro SWAP_TOOL"].current_tool to track what is physically connected to the machine.
• Workspace Transformations: Persistent CNC registers (cnc_g54_x, cnc_g54_y, cnc_g54_z) store offsets for subtractive tasks, safely isolating industrial coordinate shifts from default 3D print endstops.
🔧 Active Toolhead Modules & Software Rules
1. BlockOne (Slot 0)
• Type: DEPOSITION
• Configuration: Standard single-extruder 3D printing toolhead. Starts execution by passing explicit formatting via OrcaSlicer: START_JOB TOOLHEAD="BlockOne" MATERIAL="[filament_type]" NOZZLE_SIZE=[nozzle_diameter] EXTRUDER=0. Numbers are cleanly passed un-quoted to ensure stepper current arithmetic checks parse flawlessly.
2. SwitchFly (Slot 1)
• Type: DEPOSITION
• Configuration: Single physical stepper motor shared between two independent filament tubes. Alignments are shifted using a dedicated _SWITCHFLY_SET_PATH servo flag (0 to 180 degrees).
• The Direction-Reversal Override: Because path 1 pulls filament from the backside of the drive gears, G0 and G1 are globally intercepted using rawparams. If SwitchFly path 1 is active, extrusion targets are dynamically inverted to a negative orientation (E * -1.0) on the fly, safely preserving all travel tracking, layer speeds, and slicer width strings.
3. LightSaber (Slot 2)
• Type: LASER
• Configuration: High-frequency laser diode cutter. Integrates standard GRBL convention parameters (M3/M4/M5) scaled smoothly against laser_s_max.
• Safety Lockout: Implements hard hardware-gated overrides inside SET_LASER_POWER. If any job streams an M3 signal while a 3D printer hotend or spindle is attached, Klipper forces an immediate safety shutdown to protect the umbilical pins and user workspace. Isolates LEDFLASH from high-frequency lines to eliminate processor stutter. Features an interactive 1% duty-cycle visibility target utility (LASER_FOCUS_ALIGN).
4. HotJoe (Slot 3)
• Type: CNC
• Configuration: Brushless outrunner CNC spindle motor driven by a 400Hz open-loop RC Electronic Speed Controller (ESC). Low-endpoint throttle arms at 0.3, scaling to high-endpoint maximum thresholds at 1.0.
• Subtractive Calibration: Houses an interactive, graphical windowed CALIBRATE_ESC endpoints synchronization wizard. Integrates G54 offsets and an automated PROBE_Z_WORK_ZERO 10mm aluminum touch-plate downward search matrix.
5. DragKnife (Slot 4)
• Type: DRAG_KNIFE
• Configuration: Mechanical spring-loaded vector vinyl plotting blade. Features a dedicated, safety-gated absolute scoring utility (_DK_TEST_CUT) which drops exactly 0.3mm beneath the G54-zero material face to trace a 10mm validation cut line, protecting underlying cutting mats from relative plunge errors.
🖥️ Graphic User Experience Panels (Mainsail UI)
• SWAP_TOOL: A modular 2-stage hot-swap wizard. Shuts down heaters, cools gantry items to a safe 40°C, cuts extruder power lines to prevent pin-arcing, and pauses execution (PAUSE_BASE). It prompts the physical hand-swap before allowing verification hooks (CONFIRM_TOOL_INSTALL) to read the universal PF4 thermistor circuit line.
• PREHEAT: A dynamic pre-flight checker. If a sliced job specifies PLA, it halts execution and opens a web-interface modal allowing the operator to click a button and completely bypass build plate heating/soaking, leaping straight into the file.
• CNC_JOB_SETUP: A sequential step-by-step setup screen for machining. Guides workholding clamps, collet torque, and launches an optional dynamic choice path between touch-plate or manual paper zeroing.
• BACKUP_CONFIG: Automatically hooks into CONFIRM_TOOL_INSTALL and any successful print job that tracks an execution runtime greater than 2 hours (printer.print_stats.total_duration >= 7200). Packages and pushes the entire .cfg layout tree, macro sets, and uploaded OrcaSlicer .bb bundles straight to your remote GitHub repo over an authenticated secure SSH key tunnel (git_protocol="ssh").

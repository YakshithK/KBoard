# KBoard

An 84-key custom mechanical keyboard built from scratch around the RP2040. No dev module: the RP2040, flash, regulator, USB-C, crystal, and support circuitry are all on the board. Uses Cherry MX Browns.

![KBoard PCB top render](assets/pcb-top.png)

| Top | Bottom |
| --- | --- |
| ![PCB top view](assets/pcb-top.png) | ![PCB bottom view](assets/pcb-bottom.png) |

## Features
- 84 hot-swap MX-compatible switches in a ROW2COL matrix with per-key diodes
- From-scratch RP2040 design with USB-C, 16Mbit flash, and onboard 3.3V regulation
- QMK firmware with RP2040 USB bootloader (drag-and-drop UF2 flashing)

## Technical Details

The PCB is a basic 2-layer pcb (306 x 125 mm) using an RP2040 SoC with a USB-C connector. There's also a switch broken on the bottom for boot/reset.

![Schematic](assets/schematic.svg)

## Bill of Materials

Please see: [`BOM.csv`](BOM.csv)

## Repo Index

### Start Here

| Path | Purpose |
| --- | --- |
| [`README.md`](README.md) | Project overview, features, bill of materials, and this repository map |
| [`BOM.csv`](BOM.csv) | Bill of materials |

### Hardware: KiCad

| Path | Purpose |
| --- | --- |
| [`kboard_pcb/KBoard.kicad_pro`](kboard_pcb/KBoard.kicad_pro) | KiCad project settings |
| [`kboard_pcb/KBoard.kicad_sch`](kboard_pcb/KBoard.kicad_sch) | Source schematic |
| [`kboard_pcb/KBoard.kicad_pcb`](kboard_pcb/KBoard.kicad_pcb) | Source PCB layout |

### Hardware: CAD Files

| Path | Purpose |
| --- | --- |
| [`CAD/KBoard.step`](CAD/KBoard.step) | 3D CAD model in STEP format |
| [`PCB/KBoard.step`](PCB/KBoard.step) | 3D CAD model in STEP format |
| [`PCB/KBoard.stl`](PCB/KBoard.stl) | 3D CAD model in STL format (local only, too large for git) |

### Hardware: Production Files

| Path | Purpose |
| --- | --- |
| [`production/KBoard-gerbers.zip`](production/KBoard-gerbers.zip) | Zipped Gerbers + drill, ready to upload to the fab |
| [`production/KBoard.step`](production/KBoard.step) | STEP model bundled for fabrication |
| [`production/gerbers/`](production/gerbers/) | Gerber plot, drill, and pick-and-place files |
| [`production/firmware/`](production/firmware/) | QMK firmware source and built UF2 for flashing |

### Hardware: Visual References

| Path | Purpose |
| --- | --- |
| [`assets/schematic.svg`](assets/schematic.svg) | Schematic preview |
| [`assets/pcb-top.png`](assets/pcb-top.png) | Top-side PCB render |
| [`assets/pcb-bottom.png`](assets/pcb-bottom.png) | Bottom-side PCB render |

### Firmware: QMK

| Path | Purpose |
| --- | --- |
| [`firmware/kboard/keyboard.json`](firmware/kboard/keyboard.json) | Keyboard identity, RP2040 target, pins, matrix, and layout |
| [`firmware/kboard/rules.mk`](firmware/kboard/rules.mk) | QMK build settings |
| [`firmware/kboard/config.h`](firmware/kboard/config.h) | Board configuration |
| [`firmware/kboard/kboard.h`](firmware/kboard/kboard.h) | Keyboard header included by QMK |
| [`firmware/kboard/keymaps/default/keymap.c`](firmware/kboard/keymaps/default/keymap.c) | Default keymap |

Build the firmware with `qmk compile -kb kboard -km default` (the `firmware/kboard` folder must be linked or copied to `qmk_firmware/keyboards/kboard`). Flash the resulting UF2, also bundled at [`production/firmware/kboard_default.uf2`](production/firmware/kboard_default.uf2), by double-pressing reset and dragging it onto the USB drive.

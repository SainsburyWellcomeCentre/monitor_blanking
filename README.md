# Monitor Blanking

A TTL-controlled switch to blank a monitor display, for use in behavioural experiments.

**Note: This device is designed as a modification for monitors. Fine-tuning may be required for different models.**

![Assembled](img/assembled.png)

## Features

- Isolated TTL input up to 1MHz
- Switch on-off time < 1us
- Adjustable brightness
- Forced-on switch for testing and debugging
- Support output power up to 15W

## Online eCAD Viewer

You can view the eCAD project online using the [Altium 365 Viewer](https://sainsburywellcomecentre.github.io/fablab/).

[![View in Altium 365](https://img.shields.io/badge/View%20in-Altium%20365-blue?logo=altium&logoColor=white)](https://sainsburywellcomecentre.github.io/fablab/)

## Getting Started

<img src="img/panel.png" alt="Panel" width="300"/>

## Folder Structure

The project is structured as follows:

```bash
├── eCAD/
│   ├── Assembly/
│   │   ├── BOM.xlsx
│   │   └── pick and place.csv
│   ├── Drawing/
│   │   ├── 2d.dxf
│   │   └── 3d.step
│   ├── Fabrication/
│   │   ├── Gerber/
│   │   └── NC Drill/
│   ├── Source/
│   └── Schematic.pdf
├── mCAD/
│   ├── 3DP/
│   │   ├── ring.stl
│   │   ├── button.stl
│   │   └── base.stl
│   ├── Source/
│   └── panel_drill.dxf


```

### eCAD

This folder contains an Altium Designer project and its output files.

### mCAD

This folder contains the complete mechanical design in Inventor 2025 project formatand its output files.

## Build on your own

### Get the parts

**Note: This section is for those who don't have resources to manufacture the parts in-house and want to order them from a PCB manufacturer and 3D printing service.**

For the circuit board, we recommend using the [JLCPCB](https://jlcpcb.com/) service for PCB fabrication and assembly. If you prefer to assemble the components yourself, you can check the [Bill of Materials (BOM)](eCAD/Assembly/BOM.xlsx) file.

You can find the tutorial on how to order from JLCPCB [here](https://jlcpcb.com/capabilities/assembly).

3D printed parts can be ordered from any 3D printing service of your choice. We recommend using [JLCPCB](https://jlcpcb.com/) for their competitive pricing and quality.

### Assembly and Installation

1. Put the 'ring' under the potentiometer and insert the potentiometer into the PCB before soldering it in place. This will allow the potentiometer to align with the BNC connector.
2. Insert the 'button' into the pushbutton switch.
3. Attach the 'base' under the circuit board.
4. Open the back panel of the monitor, you will see a 6-pin cable connected to the motherboard. Unplug the 6-pin cable and connect it to the white 6-pin connector on the circuit board.
5. Solder the live and neutral wires from the monitor to the circuit board. (2 pin screw terminal)
6.

## Requirements

To access the source CAD projects, the required software for the project is as follows

- Altium Designer 24 or newer. Academic licenses can be obtained by contacting [Altium Education](https://www.altium.com/education/)
- Inventor Pro 2025 or newer. Academic licenses can be obtained by contacting [Autodesk Education](https://www.autodesk.com/education/home)

## License

Sainsbury Wellcome Centre hardware is released under [Creative Commons Share-alike 4.0 International](http://creativecommons.org/licenses/by-sa/4.0/).

Note: This is a human-readable summary of (and not a substitute for) the [license](License.txt).

You are free to:

Share — copy and redistribute the material in any medium or format
Adapt — remix, transform, and build upon the material
for any purpose, even commercially.
The licensor cannot revoke these freedoms as long as you follow the license terms.
Under the following terms:

Attribution — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.
ShareAlike — If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.
No additional restrictions — You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.
Notices:

You do not have to comply with the license for elements of the material in the public domain or where your use is permitted by an applicable exception or limitation.
No warranties are given. The license may not give you all of the permissions necessary for your intended use. For example, other rights such as publicity, privacy, or moral rights may limit how you use the material.

## Acknowledgments

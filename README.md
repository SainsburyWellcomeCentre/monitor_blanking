# Monitor Blanking

A TTL-controlled light switch designed to blank monitor displays for use in behavioural experiments.

> **Note:** This device modifies existing monitors. Some tuning may be required depending on the model.

<img src="img/assembled.png" alt="Assembled" width="800"/>

In systems neuroscience research, you want to present visual stimuli to animals without damaging the sensors you use to record neural activity. e.g. photomultiplier (PMT) for multiphoton imaging. Monitor blanking is a commonly used approach to minimize monitor light contamination by blanking the monitor backlight during the imaging pixel acquisition. The monitor turns on only during flyback periods of the fast-scan axis. Another approach is to use [a 3D-printed cone](https://labrigger.com/blog/2024/11/17/a-fantastic-shroud-for-visual-stimulation-during-imaging/).

## 🔧 Features

- Electrically isolated TTL input (up to 1 MHz)
- Sub-1 µs switching time
- Adjustable backlight brightness
- Forced-on switch for testing/debugging
- Supports up to 15 W output power

## 🌐 View Online (eCAD)

View the complete electronic design project online via [Altium 365 Viewer](https://sainsburywellcomecentre.github.io/fablab/):

[![View in Altium 365](https://img.shields.io/badge/View%20in-Altium%20365-blue?logo=altium&logoColor=white)](https://sainsburywellcomecentre.github.io/fablab/)

## 🚀 Getting Started
Connect the monitor to your computer and adjust the resolution, scaling, etc. On Windows, navigate to `Settings > System > Display`. Pressing the **Forced ON** button will enable _debug_ mode, where the monitor functions as a standard monitor without digital pulses.

<img src="img/panel.png" alt="Panel" width="300"/>

Once the monitor is detected and configured (also disable the _debug_ mode), send digital pulses from your fast-axis mirror through the **Trigger** BNC connection. A low signal will blank the monitor, and a high signal will allow backlight illumination. (hence, you cannot see anything if you are not sending TTL pulses.) Here are example functions for ScanImage users to generate and send monitor blanking TTLs. [BaselLaserMouse/ScanImageTools](https://github.com/BaselLaserMouse/ScanImageTools)

The luminance of the monitor can be measured using a luminance meter (e.g. LS-100, Konica Minolta) or a light sensor (e.g. Photodiode, Champalimaud Foundations’s Hardware Platform).

## 📁 Project Structure

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

### `eCAD/`

Contains Altium Designer source files, schematics, fabrication outputs, and documentation.

### `mCAD/`

Contains 3D mechanical designs (Inventor 2025) and printable STL models.

## 🛠️ Build It Yourself

### 1. Get the Parts

> For users without in-house fabrication capabilities.

- **PCB**: Order from [JLCPCB](https://jlcpcb.com/) (includes assembly service). Refer to the [Bill of Materials (BOM)](eCAD/Assembly/BOM.xlsx) for manual assembly.
- **3D Prints**: Print the mechanical components using any 3D printing service. JLCPCB also offers 3D printing at competitive prices.

See the [JLCPCB Assembly Tutorial](https://jlcpcb.com/capabilities/assembly) for step-by-step instructions.

### 2. Assembly & Installation

1. Place the **ring** under the potentiometer and insert it into the PCB before soldering. This ensures alignment with the BNC connector.
2. Insert the **button** into the tactile switch.
3. Attach the **base** underneath the PCB.
4. Open the monitor’s rear panel and locate the 6-pin cable connected to the motherboard. Disconnect it and plug it into the white 6-pin connector on the circuit board.
5. Connect the monitor's **live and neutral wires** to the 2-pin screw terminal on the board.
6. Drill the back panel of the monitor to accommodate the BNC, potentiometer, and pushbutton.

   Use `mCAD/panel_drill.dxf` or refer to the manual drill dimensions below:

   <p align="center">
       <img src="img/drill.png" alt="Drill Diagram" height="500"/>
   </p>

7. Mount the PCB to the panel and reassemble the monitor.

## ⚙️ Fine-Tuning the Blanking Driver

The blanking driver circuit is designed to support a wide range of monitor backlight types. However, to ensure optimal performance, you may need to fine-tune the **VLED** voltage.

### 🔧 Voltage Adjustment Guidelines

- Press the pushbutton to force the monitor **ON**, then use the trimmer **R9** to adjust the **VLED** until the backlight reaches the desired brightness level.
- The output voltage **VLED** can be adjusted within the range of **41 V to 61 V**.
  > The recommended **VLED** is at least **2 V higher** than the forward voltage of the backlight panel.

<div align="center">
  <img src="img/trimmer.png" alt="Trimmer R9" width="600"/>
</div>

## 💻 Software Requirements

To access the source CAD projects:

- **Altium Designer 24** or newer  
  Academic licenses available via [Altium Education](https://www.altium.com/education/)
- **Autodesk Inventor Pro 2025** or newer  
  Academic licenses via [Autodesk Education](https://www.autodesk.com/education/home)

## 📜 License

**Sainsbury Wellcome Centre hardware is released under** [Creative Commons Attribution-ShareAlike 4.0 International](http://creativecommons.org/licenses/by-sa/4.0/).

You are free to:

- **Share** — copy and redistribute the material in any medium or format
- **Adapt** — remix, transform, and build upon the material for any purpose

Under the following terms:

- **Attribution** — Give appropriate credit, link to the license, and indicate changes.
- **ShareAlike** — Distribute your contributions under the same license.
- **No additional restrictions** — Don’t apply legal or technological measures that prevent others from doing anything the license permits.

> For the full legal text, see [LICENSE.txt](License.txt).

## 📚 Reference
```bibtex
@ARTICLE{Leinweber2014-nf,
  title     = "Two-photon calcium imaging in mice navigating a virtual reality environment",
  author    = "Leinweber, Marcus and Zmarz, Pawel and Buchmann, Peter and Argast, Paul and Hübener, Mark and Bonhoeffer, Tobias and Keller, Georg B",
  journal   = "Journal of visualized experiments: JoVE",
  number    =  84,
  pages     = "e50885",
  month     =  feb,
  year      =  2014,
  url       =  "https://app.jove.com/t/50885/two-photon-calcium-imaging-mice-navigating-virtual-reality",
  doi       =  {10.3791/50885}
}

```

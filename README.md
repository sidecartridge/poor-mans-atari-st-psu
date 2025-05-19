# Poor Man's Atari ST PSU: A \$6 USB-C Power Supply for Your Atari ST

This guide shows how to build a simple and ultra-low-cost power supply for Atari ST/STE/Mega ST computers using off-the-shelf USB-C PD modules and buck converters—many available for under \$6 total on AliExpress or similar platforms.

> ⚠️ **WARNING:** This project comes with absolutely no warranty. Use at your own risk. The author is not responsible for any damage to your hardware or yourself. Please read this guide carefully and understand what you're doing before proceeding. If you're not confident working with electronics, consider [purchasing a commercial power supply](https://sidecartridge.com) instead.

![Atari ST PSU](/6DOLLAR-PSU-ATARI-ST-FINAL.png)

## Introduction

The Atari ST series requires:

* **+5V @ 2A** for core logic
* **+12V @ 1A** for the floppy drive, audio system, and peripherals

If you're replacing an internal PSU, this guide applies directly. If you're replacing an **external PSU**, you may also need **-12V**, which is **out of scope** for this project.

The design leverages a USB-C PD power supply (capable of negotiating higher voltages) and two buck converters to produce clean +5V and +12V outputs. If your PD source only offers 5V or 9V, **you may only get +5V output**, which means floppy drives and audio may not work.

## Components Required

* **1× USB-C PD module** (e.g. [AliExpress link](https://www.aliexpress.com/item/1005003336833794.html))
* **2× Buck converter modules** (adjustable; e.g. [AliExpress link](https://www.aliexpress.com/item/1005004904872120.html))
* **1× USB-C cable** (rated for ≥3A)
* **1× USB-C PD power supply** (capable of 15V or 20V at ≥3A)
* **1× Riser board** (optional 3D printed part)
* **4× M3 screws + nuts**, **4× M3 standoffs** (>5mm)
* **1× JST VH 2-pin female connector** (for PD module output)
* **Wiring** (3-color suggested: red, white, green)
* **1× 6-pin female connector** (reuse from original Atari PSU)

![Atari ST PSU Parts](/6DOLLAR-PSU-ATARI-ST-BOARD.png)

## Required Tools

* Multimeter (non-negotiable)
* Soldering iron (fine tip preferred)
* Screwdriver
* Wire stripper (optional)
* Heat shrink tubing + lighter/heat gun (optional)
* 3D printer (optional)

## Assembly Instructions

### Step 1: Configure the USB-C PD Module

1. Connect PD module to USB-C power supply.
2. Set it to output **15V or 20V** using jumpers/switch.
3. Verify output using a **multimeter**.

### Step 2: Prepare the Buck Converters

1. Connect both buck converters to the PD module output.
2. Adjust outputs using the potentiometers:

   * 5V converter → **Set to 5.00V**
   * 12V converter → **Set to 12.00V**
3. Share ground wire (e.g., white), use red for 5V and green for 12V.
4. Double-check voltages **with multimeter**.

### Step 3: Wire the 6-Pin Connector

Use the following pinout:

* **Pin 1:** 5V (red)
* **Pin 2:** 5V (red)
* **Pin 3–5:** GND (white)
* **Pin 6:** 12V (green)

Solder wires, insulate with heat shrink, and **verify all with multimeter**.

### Step 4: Mounting

* Optionally, 3D print a riser board to hold the PD module and buck converters. The STL file is available in the repository.
* Mount buck converters on riser board using M3 screws and standoffs.
* Reuse original PSU chassis/metal plate if possible.

### Step 5: Final Safety Checks

* Confirm all voltages.
* Check all solder joints.
* Ensure no shorts or floating wires.

### Step 6: Power On Test

* Plug in USB-C PSU.
* If the power LED turns on, proceed to test floppy, sound, etc.
* If nothing happens, disconnect immediately and recheck everything.

## Known Issues & Limitations

* **PD Source Requirements:** Must support 15V or 20V @ 3A minimum.
* **Converter Efficiency:** Slight loss; avoid underpowered adapters.
* **Heat:** Buck converters, especially the 5V one, can get hot. Add heatsinks or ensure airflow.
* **Ghosting:** Low-quality buck converters may cause video artifacts due to poor decoupling.

## Troubleshooting Tips

| Symptom                     | Suggested Fix                                     |
| --------------------------- | ------------------------------------------------- |
| No power                    | Check all voltages and connections                |
| Floppy/sound not working    | Ensure 12V is present                             |
| System crashes              | 5V may be sagging under load; check output        |
| PD module not working       | Check cable, power source, switch/jumper settings |
| Buck converter output wrong | Adjust potentiometers; verify input voltage       |
| Voltage fluctuates          | Possible poor connection or bad converter         |

## Tested Power Supplies

Feel free to add your own tested power supplies to this list. The following have been confirmed to work well with this setup:

### 15V/20V Sources

- [Baseus 65W USB-C GaN PD power supply](https://www.aliexpress.com/item/1005005030843371.html): this power supply works well with the power supply and can output 15V or 20V. It is compact and affordable.
- [Apple 96W USB-C Power Adapter](https://www.apple.com/shop/product/MW2L3AM/A/96w-usb-c-power-adapter): this power supply works well with the power supply and can output 20V. It is more expensive but is a high-quality option.
- [Apple 30W USB-C Power Adapter](https://www.apple.com/shop/product/MW2G3AM/A/30w-usb-c-power-adapter): this power supply works well with the power supply and can output 15V. It is compact and affordable.

### Below 12V (limited use case)

- [Apple 20W USB-C Power Adapter](https://www.apple.com/shop/product/MW2H3AM/A/20w-usb-c-power-adapter): this power supply works if and only if you set the USB-C PD module to 9V. 

## LICENSE

This project is licensed under the GNU General Public License - see the [LICENSE](LICENSE) file for details.

## Copyright

© 2025 GOODDATA LABS SL. All rights reserved. This project is not affiliated with Atari or any other company except for GOODDATA LABS SL and [Sidecartridge.com](https://sidecartridge.com). The Atari ST is a trademark of Atari Corporation.

# Screenshots – CMOS Inverter Design and Transient Analysis

This folder contains the screenshots used in the documentation of **Part 01 – CMOS Inverter Design and Transient Analysis**.

The images illustrate the complete workflow of designing a CMOS inverter using the **Sky130 Open-Source PDK**, generating the SPICE netlist, running transient simulation with **NgSpice**, and verifying the inverter operation through the input and output waveforms.

## Screenshot List

| Screenshot | Description |
|------------|-------------|
| `cmos_pt1_ubuntu_code.png` | Creating the project directory and copying the Sky130 `xschemrc` configuration file. |
| `cmos_pt1_xterm.png` | Launching Xterm and opening the Xschem design environment. |
| `cmos_pt1_choosing_pfet.png` | Selecting the PMOS transistor from the Sky130 device library. |
| `cmos_pt1_choosing_nfet.png` | Selecting the NMOS transistor from the Sky130 device library. |
| `cmos_pt1_selecting_labpins.png` | Adding and configuring the required lab pins (VIN, VOUT, VDD, and GND). |
| `cmos_pt1_schematic.png` | Completed CMOS inverter schematic in Xschem. |
| `cmos_pt1_choosing_source.png` | Adding and configuring the voltage source for transient simulation. |
| `cmos_pt1_codeshown.png` | Simulation code block (`code_shown.sch`) containing the SPICE simulation commands. |
| `cmos_pt1_nelist.png` | Generated SPICE netlist before simulation. |
| `cmost_pt1_ngspice_simulation_window.png` | NgSpice simulation window after successful execution. |
| `cmos_pt1_plotting vin vout.png` | Transient waveform showing the input (VIN) and output (VOUT) signals of the CMOS inverter. |

---

## Tools Used

- Xschem
- NgSpice
- Sky130 Open-Source PDK
- Ubuntu Linux

---

These screenshots are referenced throughout the **01_README.md** document to demonstrate each stage of the CMOS inverter design and transient simulation workflow.

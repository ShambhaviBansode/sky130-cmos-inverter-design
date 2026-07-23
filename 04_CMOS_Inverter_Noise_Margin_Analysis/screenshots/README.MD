# Screenshots – CMOS Inverter Noise Margin Analysis

This folder contains the screenshots used in the documentation of **Part 04 – CMOS Inverter Noise Margin Analysis**.

This experiment extends the **Voltage Transfer Characteristics (VTC)** analysis performed in **Part 03** by evaluating the gain curve and calculating the noise margins of the CMOS inverter. The screenshots document the complete workflow, including simulation execution, gain analysis, identification of the critical voltages (**VIL** and **VIH**), and determination of the high and low noise margins.

## Screenshot List

| Screenshot | Description |
|------------|-------------|
| `cmos_pt4_ubuntu_and_xterm_code_for_opening_file.png` | Opening the existing CMOS inverter project and launching Xschem from the Ubuntu terminal. |
| `cmos_pt4_netlist.png` | Generated SPICE netlist used for the noise margin analysis. |
| `cmos_pt4_simulation_window2.png` | NgSpice simulation window after executing the DC sweep simulation. |
| `cmos_pt4_gain_curve.png` | Gain curve obtained by plotting the derivative of the VTC curve. |
| `cmos_pt4_gain_vout_combined.png` | Combined plot showing the gain curve and VTC used to determine **VIL** and **VIH**. |
| `cmos_pt4_upper_lower_side_noise_margin.png` | Final calculation of the high-side and low-side noise margins of the CMOS inverter. |

---

## Tools Used

- Xschem
- NgSpice
- Sky130 Open-Source PDK
- Ubuntu Linux

---

These screenshots are referenced throughout the **04_README.md** document to illustrate each stage of the CMOS inverter noise margin analysis workflow.

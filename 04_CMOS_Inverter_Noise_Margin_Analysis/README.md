# 04 – CMOS Inverter Noise Margin Analysis

## Objective

This section is a continuation of **Part 03 – CMOS Inverter Voltage Transfer Characteristics (VTC)**. The VTC obtained in the previous experiment is used to calculate the gain curve and determine the **Noise Margins** of the CMOS inverter. Noise margin is an important performance parameter that indicates the immunity of a digital circuit against unwanted noise.

---

## Prerequisite

This experiment uses the same CMOS inverter schematic and testbench developed in **Part 03**. Only the simulation commands and post-processing in NgSpice are extended to calculate the gain curve and determine the values of **VIL**, **VIH**, **NML**, and **NMH**.

---

# Analysis Flow

## Step 1: Opening the Existing CMOS Inverter Testbench

The CMOS inverter project created in Part 03 was opened from the Ubuntu terminal. Since the schematic and testbench were already available, the existing design was reused for noise margin analysis.

<table>
<tr>
<td align="center">

**Opening the Project**

<img src="screenshots/cmos_pt4_ubuntu_and_xterm_code_for_opening_file.png" width="750">

</td>
</tr>
</table>

---

## Step 2: Netlist Generation

After verifying the schematic connections, Xschem generated the SPICE netlist. The generated netlist contains all transistor models, power supplies, simulation commands, and circuit connectivity required by NgSpice.

<table>
<tr>
<td align="center">

**Generated Netlist**

<img src="screenshots/cmos_pt4_netlist.png" width="700">

</td>
</tr>
</table>

---

## Step 3: Running the Simulation

The DC sweep simulation was executed using NgSpice. The previously generated Voltage Transfer Characteristic (VTC) was used as the basis for further gain and noise margin calculations.

<table>
<tr>
<td align="center">

**Simulation Window**

<img src="screenshots/cmos_pt4_simulation_window2.png" width="700">

</td>
</tr>
</table>

---

## Step 4: Plotting the Gain Curve

The gain of the CMOS inverter was calculated by taking the derivative of the output voltage with respect to the input voltage.

The following NgSpice commands were used:

```spice
plot derive(v(vout))

let gain = abs(derive(v(vout)))

plot gain
```

The gain curve identifies the region where the magnitude of the voltage gain exceeds unity.

<table>
<tr>
<td align="center">

**Gain Curve**

<img src="screenshots/cmos_pt4_gain_ciurve.png" width="650">

</td>
</tr>
</table>

---

## Step 5: Determining VIL and VIH

The points where the magnitude of the gain becomes equal to one were identified.

These voltages correspond to:

- **VIL** – Maximum input voltage recognized as Logic LOW.
- **VIH** – Minimum input voltage recognized as Logic HIGH.

These values define the valid operating region of the CMOS inverter.

<table>
<tr>
<td align="center">

**Gain Curve with VTC**

<img src="screenshots/cmos_pt4_gain_vout_combined.png" width="700">

</td>
</tr>
</table>

---

## Step 6: Noise Margin Calculation

Using the measured values of **VIL** and **VIH**, the inverter noise margins were calculated as

- **Low Noise Margin (NML)**

  NML = VIL − VOL

- **High Noise Margin (NMH)**

  NMH = VOH − VIH

A balanced pair of noise margins indicates good robustness of the CMOS inverter against unwanted input noise.

<table>
<tr>
<td align="center">

**Upper and Lower Noise Margins**

<img src="screenshots/cmos_pt4_gain_vout_combined.png" width="700">

</td>
</tr>
</table>

---

# Observation

- The Voltage Transfer Characteristic obtained in Part 03 was reused for the analysis.
- The gain curve was obtained by differentiating the VTC.
- The points where **|Gain| = 1** were identified to determine **VIL** and **VIH**.
- The calculated **Noise Margins (NML and NMH)** indicate the tolerance of the inverter to external noise.
- A nearly symmetrical noise margin confirms good switching characteristics and reliable digital operation.

---

# Conclusion

This experiment extends the Voltage Transfer Characteristic (VTC) analysis performed in **Part 03** by evaluating the noise margins of the CMOS inverter. The gain curve was analyzed to determine the critical switching voltages (**VIL** and **VIH**), and the corresponding **Low Noise Margin (NML)** and **High Noise Margin (NMH)** were calculated. These parameters are essential for assessing the reliability and robustness of CMOS digital circuits and form an important step in the complete CMOS inverter characterization workflow.

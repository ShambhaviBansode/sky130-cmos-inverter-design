# 05 – CMOS Inverter Transient (Delay) Analysis

## Objective

The objective of this experiment is to analyze the **dynamic switching behavior** of a CMOS inverter using **Transient Analysis** in Xschem and NGSPICE. Unlike DC analysis, which studies the steady-state characteristics of the inverter, transient analysis evaluates how the output responds to a time-varying input signal.

The experiment also measures the **Propagation Delay (tPHL)** of the inverter by determining the time difference between the 50% transition points of the input and output waveforms.

---

## Theory

A CMOS inverter does not switch instantaneously due to the presence of parasitic and load capacitances. When the input changes, the output capacitor must either charge through the PMOS transistor or discharge through the NMOS transistor.

This charging and discharging process introduces a finite delay known as the **Propagation Delay**.

For an inverter:

- **tPHL** – Propagation delay when the output transitions from **High to Low**.
- **tPLH** – Propagation delay when the output transitions from **Low to High**.

Propagation delay is measured between the **50% voltage levels** of the input and output waveforms.

For a supply voltage of **1.8 V**,

\[
V_{50\%}=0.5\times1.8=0.9\;V
\]

Therefore,

\[
t_{PHL}=t_{OUT(50\%)}-t_{IN(50\%)}
\]

---

## Circuit Schematic

The CMOS inverter schematic consists of:

- PMOS transistor connected to VDD
- NMOS transistor connected to Ground
- Pulse voltage source as input
- Output node connected to both transistors

Insert the schematic screenshot below.

> **Screenshot:** `cmos_pt5_schematic.png`

---

## Editing the Input Source

To perform transient analysis, the DC input source is replaced with a **Pulse Voltage Source**.

The pulse source used is:

```spice
pulse(0 1.8 1ns 1ns 5ns 10ns)
```

where

- Initial Voltage = **0 V**
- Final Voltage = **1.8 V**
- Delay Time = **1 ns**
- Rise Time = **1 ns**
- Pulse Width = **5 ns**
- Time Period = **10 ns**

> **Screenshot:** `cmos_pt5_editing_source_sym_vin.png`

---

## Editing the Simulation Code

The simulation command is changed from DC analysis to **Transient Analysis**.

Example:

```spice
.tran 0.02n 10n
```

where

- Time Step = **0.02 ns**
- Stop Time = **10 ns**

> **Screenshot:** `cmos_pt5_editing_code_shown_block.png`

---

## Generated Netlist

After saving the schematic, Xschem automatically generates the SPICE netlist used by NGSPICE.

The generated netlist contains:

- MOSFET definitions
- Power supply
- Pulse input source
- Model library
- Transient simulation command

> **Screenshot:** `cmos_pt5_edited_netlist.png`

---

## Running the Simulation

After generating the netlist, launch NGSPICE and execute the transient simulation.

```
ngspice inv_test2.spice
```

The simulator computes the node voltages for each time step and stores the transient waveform data.

> **Screenshot:** `cmos_pt5_simulation_window.png`

---

## Selecting the Transient Plot

Since multiple analyses may exist, first list the available plots.

```spice
setplot
```

Output:

```
List of plots available:

Current tran1
Analysis transient
```

Switch to the transient plot.

```spice
setplot tran1
```

---

## Plotting the Input and Output Waveforms

The input and output waveforms are plotted together using

```spice
plot vin vout
```

This graph shows the delay between the input transition and the output transition.

> **Screenshot:** `cmos_pt5_plotting_vin_vout.png`

---

## Measuring the 50% Input Crossing

The input reaches 50% of the supply voltage at

```spice
meas tran vin50 when vin=0.9 RISE=2
```

Measured value:

```
vin50 = 6.75000e-09 s
```

---

## Measuring the 50% Output Crossing

The output reaches 50% of the supply voltage at

```spice
meas tran vout50 when vout=.9 FALL=2
```

Measured value:

```
vout50 = 6.77488e-09 s
```

---

## Calculating the Propagation Delay

Propagation delay is calculated as

\[
t_{PHL}=t_{OUT(50\%)}-t_{IN(50\%)}
\]

Using the measured values,

\[
t_{PHL}
=
6.77488\times10^{-9}
-
6.75000\times10^{-9}
\]

\[
t_{PHL}=2.4882\times10^{-11}\;s
\]

which is

\[
\boxed{t_{PHL}=24.882\;ps}
\]

The calculation can also be performed directly in NGSPICE using

```spice
let tphl=vout50-vin50
```

Print the result

```spice
print tphl
```

Output

```
tphl = 2.488200e-11
```

> **Screenshot:** `cmos_pt5_simulation_window.png`

---

## Observation

- The output does not switch instantaneously after the input transition.
- The delay occurs because the load capacitance requires finite time to charge and discharge through the PMOS and NMOS transistors.
- The measured High-to-Low propagation delay is approximately **24.882 ps**.
- The transient waveform confirms the expected switching behavior of the CMOS inverter.

---

## Conclusion

Transient analysis was successfully performed using **Xschem** and **NGSPICE**. The input pulse signal was applied to the CMOS inverter, and the corresponding output waveform was observed. The propagation delay was measured using the 50% voltage crossing method.

### Final Results

| Parameter | Measured Value |
|-----------|---------------:|
| Supply Voltage | **1.8 V** |
| 50% Voltage Level | **0.9 V** |
| Input 50% Crossing Time | **6.75000 ns** |
| Output 50% Crossing Time | **6.77488 ns** |
| Propagation Delay (tPHL) | **24.882 ps** |

The measured delay demonstrates the finite switching speed of the CMOS inverter and validates its transient performance.

#  4-bit R-2R DAC Using Two-Stage CMOS Op-Amp

This project presents the **design and simulation of a 4-bit R-2R Digital-to-Analog Converter (DAC)** using a **two-stage CMOS operational amplifier** implemented in **Cadence Virtuoso (180 nm CMOS process)**.  
It demonstrates accurate digital-to-analog conversion through resistor ladder principles combined with high-gain analog amplification.

---

##  Project Overview

- **Title:** Design and Implementation of 4-bit R-2R DAC using Two-Stage Op-Amp  
- **Tool Used:** Cadence Virtuoso  
- **Technology:** 180 nm CMOS (gpdk180)  
- **Objective:** To design a low-power, high-gain DAC that converts digital input bits into proportional analog voltage.  
- **Category:** Analog / Mixed-Signal VLSI Design  

---

##  Introduction

The **R-2R ladder DAC** is a simple and effective Digital-to-Analog Converter that uses only two resistor values, *R* and *2R*, arranged in a repetitive ladder pattern.  
Each digital input bit controls a switch connecting either the reference voltage (**Vref**) or ground (**GND**) to the ladder network.

A **Two-Stage Operational Amplifier** converts the output current of the ladder into an analog voltage and provides the required amplification.

###  Stages of the Op-Amp
1. **Differential Amplifier (Input Stage)** – Amplifies the difference between inputs and rejects common-mode noise.  
2. **Common-Source Amplifier (Output Stage)** – Provides higher gain and output swing.  

Together, these stages ensure precise, linear, and stable analog output suitable for mixed-signal applications.

---

##  Working Principle

The DAC operates on the principle of **voltage division and current summation** through a network of *R* and *2R* resistors.  
Each bit’s contribution is weighted based on its binary significance:

\[
V_{out} = V_{ref} \times \left(\frac{b_3}{2} + \frac{b_2}{4} + \frac{b_1}{8} + \frac{b_0}{16}\right)
\]

where \(b_3\)–\(b_0\) are the binary input bits.

The combined output current is converted into a voltage by the op-amp, producing an analog signal proportional to the digital input.

---

##  Methodology

### 1. Design Flow in Cadence Virtuoso
- Technology: **gpdk180 (180 nm CMOS)**
- Schematic design using **analogLib** and **gpdk180** components  
- Transistor sizing based on required gain, bandwidth, and output swing  
- Layout design and post-layout simulation (parasitic-aware analysis)  
- Validation using **Transient** and **AC Analysis**

### 2. Two-Stage Op-Amp Design
| Stage | Function | Key Features |
|:------|:----------|:--------------|
| Differential Amplifier | Input stage | High CMRR, initial gain |
| Common-Source Amplifier | Output stage | Large voltage gain, high drive strength |
| Compensation | Stability | Miller capacitor ensures phase margin > 60° |

### 3. Design Considerations
1. **Resistor Matching:** High precision (≤ 0.1 %) required to minimize non-linearity.  
2. **Reference Voltage:** Low-noise, stable Vref ensures output accuracy.  
3. **Op-Amp Bias Current:** Must be small to avoid offset errors.  
4. **Gain & Bandwidth:** High open-loop gain (> 60 dB) and adequate bandwidth for fast settling.

---

##  Components Used

| Component | Library | Parameters / Value | Quantity |
|:-----------|:----------|:------------------|:----------|
| NMOS | gpdk180 | CSA – W=10 µm L=1 µm; DA – W=3 µm L=1 µm | 5 |
| PMOS | gpdk180 | CSA – W=50 µm L=1 µm; DA – W=15 µm L=1 µm | 3 |
| Resistors | gpdk180 | R = 1 kΩ, 2 kΩ | 7 |
| Vdc | analogLib | 900 mV / 1.8 V | 3 |
| Vsin | analogLib | 500 µV, 1 kHz | 1 |

---

##  Circuit Design and Simulations

### 🔹 R-2R Ladder DAC Schematic
![R-2R Ladder DAC Schematic](![WhatsApp Image 2025-11-05 at 10 19 47_d32c0b95](https://github.com/user-attachments/assets/dd89140a-0613-45ad-a3d0-7dc072b72ac2)
)

### 🔹 Two-Stage Op-Amp Schematic
![Two-Stage Op-Amp Schematic](![WhatsApp Image 2025-11-05 at 10 18 00_3c13cc3c](https://github.com/user-attachments/assets/e5974117-dce1-40bb-b02f-1cbae66d7e69)
)

### 🔹 Test Bench Setup
![Test Bench Setup](![WhatsApp Image 2025-11-05 at 10 19 14_e7cb76eb]![WhatsApp Image 2025-11-05 at 10 21 02_80d85138](https://github.com/user-attachments/assets/10157879-04a9-4bcf-bbdc-4901115d2eeb)
)
)

---

##  Simulation Results

### 🔸 Transient Analysis of dac
Displays analog voltage corresponding to digital input transitions.  
![Transient Analysis](![WhatsApp Image 2025-11-05 at 10 21 33_844770f3](https://github.com/user-attachments/assets/d6bc0ad8-6d43-46cc-bcc9-301dead451a2)
)

### 🔸 AC Analysis
Shows frequency response of:
- Differential Amplifier  
- Common-Source Amplifier  
- Complete Op-Amp  
![AC Analysis - Differential Amplifier ( ![Uploading WhatsApp Image 2025-11-05 at 10.23.15_de699d28.jpg…]()

![AC Analysis - Op-Amp] ![WhatsApp Image 2025-11-05 at 10 24 01_4e0ce29f](https://github.com/user-attachments/assets/34320f97-fc1c-4ddd-ae51-f7095c74e4c6)




---

##  References

1. B. Razavi, *Design of Analog CMOS Integrated Circuits*  
2. R. Jacob Baker, *CMOS: Circuit Design, Layout, and Simulation*  
3. Cadence Design System Documentation  
4. IEEE Papers on Low-Power DAC and Op-Amp Design  

---

## 👨‍💻 Author

**Shivabasavesh A S**  
B.E. Electronics and Communication Engineering  
The National Institute of Engineering, Mysuru  

---


---




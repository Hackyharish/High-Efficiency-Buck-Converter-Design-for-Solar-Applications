# High-Efficiency Buck Converter Design with SiC MOSFETs for Solar Applications  
![Work in Progress](https://img.shields.io/badge/status-work%20in%20progress-brightgreen?style=for-the-badge)

### MATLAB/Simulink Simulation Project

**Authors:**  
Harish R — cb.en.u4eee23112@cb.students.amrita.edu  
Karthik K — cb.en.u4eee23116@cb.students.amrita.edu  
**Institution:** Amrita School of Engineering, Coimbatore, India

---

## 📘 Overview

This repository contains the **MATLAB/Simulink model** and **supporting files** for the paper *“High-Efficiency Buck Converter Design with SiC MOSFETs for Solar Applications.”*

The project focuses on the **design and simulation of a high-efficiency synchronous buck converter** for solar battery charging. It integrates **Silicon Carbide (SiC) MOSFETs**, a **Perturb & Observe (P&O)** MPPT algorithm, and a **three-stage battery charging controller** to maximize solar energy utilization and ensure safe charging.

---

## ⚡ Abstract

Solar photovoltaic (PV) systems suffer from fluctuating output and conversion inefficiencies.  
This work presents a **high-efficiency synchronous buck converter** designed to charge a **12V lead-acid battery** from a **180W solar PV panel**.  
Replacing conventional silicon devices with **SiC MOSFETs** reduces switching and conduction losses while enabling high-frequency operation.  

The converter integrates:
- **Perturb & Observe MPPT** for maximum energy extraction  
- **Multi-stage charging (Bulk, Absorption, Float)** for battery health  
- **SiC MOSFET switching** for reduced losses and higher power density  

Simulations in **MATLAB/Simulink** demonstrate efficiency above **97%** and excellent voltage regulation across various irradiance levels.

---

## 🧠 System Architecture and Design

### 🔹 Design Overview

The proposed system is designed for **solar PV battery charging** using a high-efficiency synchronous buck converter with **SiC MOSFETs**. It includes three major functional blocks:

1. **Solar PV Generation and Modeling**  
   - Simulated using a single-diode equivalent model.  
   - Variable irradiance and temperature to replicate real-world conditions.

2. **Synchronous Buck Converter**  
   - Uses **SiC MOSFETs** for low switching losses.  
   - Steps down ~37V PV output to 14.4V battery charging voltage.  
   - Operates in **Continuous Conduction Mode (CCM)** for high efficiency.  

3. **MPPT & Battery Control**  
   - Employs **Perturb and Observe (P&O)** algorithm for real-time MPP tracking.  
   - Implements a **three-stage charging algorithm** for safe and efficient battery management.

### 🔹 System Block Diagram
![System Design](Results/system_design.png)

---

## 🔩 Converter Design and Calculations

The converter was designed based on the following **key specifications**:

| Parameter | Symbol | Value |
|------------|---------|-------|
| PV Panel Power | Pmax | 180 W |
| PV Voltage at MPP | Vmpp | 37 V |
| Battery Voltage | Vout | 14.4 V |
| Output Current | Iout | 12.5 A |
| Switching Frequency | fsw | 50 kHz |
| Inductor Ripple | ΔIL | 10% of Iout |
| Output Voltage Ripple | ΔVo | < 1% |

### ⚙️ 1. Duty Cycle
D = Vout / Vin = 14.4 / 37 = **0.389**

### ⚙️ 2. Inductor Design
L = Vout × (1 - D) / (fsw × ΔIL)  
= 14.4 × (1 - 0.389) / (50,000 × 1.25) = **141 µH**  
A **150 µH** inductor was selected as the standard value.

### ⚙️ 3. Output Capacitor Design
Cout(min) = ΔIL / (8 × fsw × ΔVo)  
= 1.25 / (8 × 50,000 × 0.144) = **21.7 µF**  
A **220 µF low-ESR capacitor** was chosen to handle transient loads and maintain ripple below 1%.

### ⚙️ 4. Efficiency Targets
The converter is designed to achieve:
- **>97% efficiency** at nominal irradiance (1000 W/m²)  
- **Minimal voltage ripple (<1%)**  
- **Stable CCM operation** under variable irradiance

---

## 📈 Simulation Setup (MATLAB/Simulink)

**Software Requirements**
- MATLAB R2023b or later  
- Simscape Electrical Toolbox  
- Control System Toolbox (for PI control)  

**Main Blocks**
1. **PV Array Model**  
2. **SiC-Based Buck Converter**  
3. **P&O MPPT Controller**  
4. **Battery Charging Logic (FSM)**  

**Simulation Scenarios**
- Irradiance: 400 W/m² – 1000 W/m²  
- Temperature: 25 °C (nominal)  
- Battery SOC transitions through Bulk → Absorption → Float

---

## 📊 Simulation Models and Results

### 🔹 Simulink Model Overview
![Simulink Model](Results/simulink_model.png)

### 🔹 MPPT Power Tracking
![PV Power Tracking](Results/mppt_power_tracking.png)

### 🔹 Converter Performance (1000 W/m²)
![Output Waveforms 1000W](Results/output_waveforms_1000w.png)
![Input Waveforms 1000W](Results/input_waveforms_1000w.png)

### 🔹 Converter Performance (800 W/m²)
![Output Waveforms 800W](Results/output_waveforms_800w.png)
![Input Waveforms 800W](Results/input_waveforms_800w.png)

### 🔹 Converter Performance (600 W/m²)
![Output Waveforms 600W](Results/output_waveforms_600w.png)
![Input Waveforms 600W](Results/input_waveforms_600w.png)

### 🔹 Converter Performance (400 W/m²)
![Output Waveforms 400W](Results/output_waveforms_400w.png)
![Input Waveforms 400W](Results/input_waveforms_400w.png)

### 🔹 Battery Charging Stages
![Battery Charging Phases](Results/battery_charging_stages.png)

---

## ⚙️ Performance Summary

| Irradiance (W/m²) | Vin (V) | Iin (A) | Vout (V) | Iout (A) | Efficiency (%) |
|--------------------|---------|---------|----------|----------|----------------|
| 1000 | 36.7 | 4.89 | 14.47 | 12.11 | **97.66** |
| 800 | 36.73 | 3.91 | 14.42 | 8.94 | **96.17** |
| 600 | 36.5 | 2.9 | 14.35 | 7.28 | **97.14** |
| 400 | 36.26 | 1.96 | 14.31 | 4.76 | **95.6** |

---

## 🧩 Advantages of SiC MOSFETs

| Property | Benefit |
|-----------|----------|
| High breakdown voltage | Enables compact, high-power design |
| Low RDS(on) | Reduces conduction losses |
| Fast switching | Minimizes dynamic losses |
| High thermal conductivity | Improves reliability and cooling efficiency |

---

## 📂 Repository Structure

```
High_Efficiency_Buck_Converter_SiC/
│
├── 📜 README.md
│
├── 📁 Simulink_Model/
│   └── buck_converter_sic.slx
│
├── 📁 Results/
│   ├── system_design.png
│   ├── simulink_model.png
│   ├── mppt_power_tracking.png
│   ├── output_waveforms_1000w.png
│   ├── input_waveforms_1000w.png
│   ├── output_waveforms_800w.png
│   ├── input_waveforms_800w.png
│   ├── output_waveforms_600w.png
│   ├── input_waveforms_600w.png
│   ├── output_waveforms_400w.png
│   ├── input_waveforms_400w.png
│   └── battery_charging_stages.png
│
└── 📄 References.pdf
```

## 🚀 Future Work

- Include **thermal modeling** of SiC devices  
- Explore **adaptive MPPT algorithms** (Incremental Conductance, Fuzzy Logic)  
- Develop a **hardware prototype** for validation  

---

## 🧾 References

1. M. H. Rashid, *Power Electronics: Circuits, Devices, and Applications*, 4th Ed., Pearson, 2013.  
2. N. Mohan, T. M. Undeland, W. P. Robbins, *Power Electronics: Converters, Applications, and Design*, 3rd Ed., Wiley, 2003.  
3. T. Esram, P. L. Chapman, *Comparison of PV MPPT Techniques*, IEEE Trans. Energy Conversion, 2007.  
4. J. W. Palmour, *SiC Power Device Development*, IEEE IEDM, 2014.

---


---

## 🏁 Conclusion

The **SiC-based synchronous buck converter** integrated with **MPPT** and **multi-stage charging** control achieved:
- Efficiency > 97%  
- Stable operation under varying irradiance  
- Low voltage ripple and reliable charging  

This validated **MATLAB/Simulink model** offers a strong foundation for developing **high-efficiency solar energy systems** with advanced semiconductor technologies.

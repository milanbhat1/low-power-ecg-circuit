# Cardio Tracker - Low-Power ECG Circuit

This project documents the design, simulation, and hardware implementation of a low-power analog ECG (Electrocardiogram) signal acquisition circuit, named **Cardio Tracker**. The system captures heart activity and displays key waveform features such as P-waves, QRS complexes, and T-waves with low noise and high clarity.

---

## Table of Contents

- [1. Introduction](#1-introduction)
- [2. Working Methodology](#2-working-methodology)
- [3. Circuit Simulation](#3-circuit-simulation)
- [4. Hardware Implementation](#4-hardware-implementation)
- [5. Inference](#5-inference)
- [6. Conclusion](#6-conclusion)
- [7. References](#7-references)
- [8. Contributors](#8-contributors)

---

## 1. Introduction

An electrocardiogram (ECG) records the heart’s electrical activity via skin electrodes. These signals are typically weak and noisy, requiring amplification and filtering.

This project focuses on building a **two-stage ECG circuit** comprising:
- Instrumentation Amplifier
- Low-Pass Filter

The objective is to deliver a clear ECG signal suitable for portable and battery-powered health monitoring applications.

---

## 2. Working Methodology

### Stage 1: Instrumentation Amplifier

- Amplifies low-level differential signals
- High Common Mode Rejection Ratio (CMRR)
- Gain set to approximately 1000
- Essential for boosting ECG signal for further processing

**Circuit Diagram:**

<img src="images/ina_circuit.png" width="600"/>

---

### Stage 2: Low-Pass Filter

- Attenuates high-frequency noise (e.g., EMG interference)
- Second-order filter with 150 Hz cutoff (per AHA guidelines)
- Helps clean the amplified ECG signal before visualization

**Circuit Diagram:**

<img src="images/lpf_circuit.png" width="600"/>

---

## 3. Circuit Simulation

Simulation was performed using **LTspice**. The ECG waveform was applied using a `.txt` file as a voltage source to mimic a real cardiac signal.

### AC Analysis Output (Low-Pass Filter)

<img src="images/transient_output_lpf.png" width="600"/>

### Transient Analysis Output

<img src="images/trasient_analysis_output.png" width="600"/>

### AC Analysis Output

<img src="images/ac_analysis_output.png" width="600"/>

### Simulation Files

- [`ecg_circuit.asc`](simulations/ecg_circuit.asc) – LTspice simulation circuit
- [`ECG_input.txt`](simulations/ECG_input.txt) – File-based input ECG waveform

---

## 4. Hardware Implementation

The circuit was constructed on a breadboard using both stages. The output shown below reflects the **combined result** of the instrumentation amplifier and low-pass filter stages.

### Key Testing Notes:

- ECG input from human subject (Lead II configuration)
- 9V batteries used for electrical safety
- Electrodes placed on right wrist, left ankle, and ground on right ankle
- Output monitored using an oscilloscope

### Hardware Setup Image

<img src="images/hardware_setup.png" width="600"/>

### Combined Output from INA + LPF Stage

<img src="images/hardware_combined_output.png" width="600"/>

### Human Subject with Electrodes

<img src="images/person_with_patches.png" width="500"/>

---

## 5. Inference

- The **INA successfully amplified** the weak ECG signals
- The **low-pass filter cleaned** the signal by reducing high-frequency noise
- In simulation, both stages were analyzed separately for clarity
- In hardware, both stages were connected and tested together
- Final waveform included visible P-waves, QRS complexes, and T-waves

---

## 6. Conclusion

The **Cardio Tracker** circuit effectively demonstrates how a simple low-power analog chain can capture reliable ECG signals. With minimal components and battery safety, the system can be adapted for portable or wearable ECG monitoring.

Future improvements:
- Integrating digital filtering (DSP) for better accuracy
- Adding wireless communication (e.g., Bluetooth)
- Designing a compact PCB for wearable implementation

---

## 7. References

1. [IEEE Xplore: Low-Power ECG Circuit Design](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9531733)  
2. [Instructables - ECG Circuit](https://www.instructables.com/Electrocardiogram-ECG-Circuit/)  
3. [Instructables - ECG Circuit (Part 2)](https://www.instructables.com/Electrocardiogram-ECG-Circuit-2/)  
4. [Instructables - ECG Circuit (Part 3)](https://www.instructables.com/Electrocardiogram-ECG-Circuit-3/)

---

## 8. Contributors

- Pranav Maruti Shanbhag (USN: 4NI24EC407)  
- Adithya Y (USN: 4N23EC005)  
- Anirudha Jayaprakash (USN: 4NI23EC014)   
- Aneesh R Kulkarni (USN: 4NI23EC013)  

# Low-Power ECG Circuit

This repository contains the design, simulation, and documentation for a low-power analog ECG (Electrocardiogram) circuit. The project focuses on amplifying and filtering bio-potential signals from the human body to capture clean, interpretable ECG waveforms. This design is well-suited for low-cost, portable, and wearable medical applications.

---

## Table of Contents

- [1. Introduction](#1-introduction)
- [2. Circuit Design](#2-circuit-design)
- [3. Circuit Integration and Testing](#3-circuit-integration-and-testing)
- [4. Simulation Results](#4-simulation-results)
- [5. Hardware Results](#5-hardware-results)
- [6. Inference](#6-inference)
- [7. Conclusion](#7-conclusion)
- [8. References](#8-references)
- [9. Contributors](#9-contributors)

---

## 1. Introduction

An electrocardiogram (ECG) is a diagnostic technique used to monitor the electrical activity of the heart. The ECG waveform consists of characteristic components such as the P-wave, QRS complex, and T-wave, which represent different phases of the cardiac cycle.

Due to the low amplitude of these signals and the presence of external/internal noise, effective signal conditioning is necessary. This project presents a three-stage, low-power ECG circuit with:

- High gain instrumentation amplification
- Notch filtering of 60 Hz powerline noise
- Low-pass filtering of high-frequency muscle artifacts

---

## 2. Circuit Design

### 2.1 Instrumentation Amplifier (INA)

- Amplifies low-level differential ECG signals
- Provides high Common Mode Rejection Ratio (CMRR)
- Gain set to approximately 1000 using precision resistors

**Circuit Diagram:**

![Instrumentation Amplifier Circuit Diagram](images/ina_circuit.png)

**Simulation Output:**

![INA Simulation Output](images/ina_sim_output.png)

---

### 2.2 Notch Filter

- Removes 60 Hz powerline interference
- Designed with center frequency f₀ = 60 Hz and Q = 8
- Targets a narrow frequency band without distorting the overall signal

**Circuit Diagram:**

![Notch Filter Circuit Diagram](images/notch_filter_circuit.png)

**Simulation Output:**

![Notch Filter Simulation Output](images/notch_filter_sim_output.png)

---

### 2.3 Low-Pass Filter

- Attenuates high-frequency noise (e.g., muscle tremors)
- Second-order configuration with a 150 Hz cutoff
- Meets AHA guidelines for ECG signal clarity

**Circuit Diagram:**

![Low-Pass Filter Circuit Diagram](images/lpf_circuit.png)

**Simulation Output:**

![Low-Pass Filter Simulation Output](images/lpf_sim_output.png)

---

## 3. Circuit Integration and Testing

The circuit stages are connected as follows:
```
Instrumentation Amplifier → Notch Filter → Low-Pass Filter
```

### Testing Methods

1. **LTspice Simulation Input**  
   - The ECG waveform was applied using a file-based voltage source in LTspice (`PWL` input with ECG waveform data).
   - This mimicked a realistic ECG signal without requiring an external function generator.

2. **Real ECG Input (Human Subject)**  
   - Lead II configuration:
     - Right wrist → Negative input  
     - Left ankle → Positive input  
     - Right ankle → Ground  
   - Use of 9V battery power for safety

### Expected Output

- Clean ECG waveform with visible:
  - P-wave
  - QRS complex
  - T-wave

---

## 4. Simulation Results

- Stage-wise outputs show:
  - Amplification of weak ECG signals
  - Suppression of 60 Hz interference
  - Reduction of high-frequency noise

- Final waveform exhibits:
  - P-wave
  - QRS complex
  - T-wave

**Complete Simulation Output:**

![Complete ECG Simulation Output](images/complete_simulation_output.png)

---

## 5. Hardware Results

During practical hardware implementation, the **notch filter stage was removed**. Although the simulation showed successful 60 Hz suppression, the actual notch filter did not behave as expected. It failed to attenuate the 60 Hz interference consistently and introduced distortion in the ECG signal. This may be due to component inaccuracies, low Q-factor realization, or real-world impedance mismatches.

As a result, only the **instrumentation amplifier** and the **low-pass filter** were used in the hardware prototype, which still produced usable ECG signals for basic visualization.

### Observations:

- Output waveforms still showed recognizable P-waves, QRS complexes, and T-waves.
- Powerline noise was partially mitigated using physical isolation and battery-based power supply.
- Patch cords and disposable electrodes were used for human testing.
- The subject was in a resting position, and care was taken to avoid motion artifacts.

**Hardware Setup Image:**

![Hardware Setup](images/hardware_setup.png)

**Oscilloscope Output (Human Subject):**

![ECG Hardware Output](images/hardware_output_waveform.png)

**Test Subject with Electrodes:**

![Test Subject](images/person_with_patches.png)

---

## 6. Inference

- The ECG circuit effectively captured and processed real-time cardiac signals.
- Amplification and low-pass filtering alone were sufficient for a basic ECG waveform.
- Simulation and hardware performance were generally consistent except for the notch filter stage.

---

## 7. Conclusion

This project demonstrates that a low-power, analog ECG circuit can be constructed using readily available components to acquire clear cardiac signals. The instrumentation amplifier and low-pass filter stages performed reliably. Future improvements could include:

- Replacing the notch filter with a better-designed active filter
- Integrating digital signal processing (DSP) for adaptive filtering
- Creating a wearable version of the circuit

---

## 8. References

1. [IEEE Xplore - Low-Power ECG Circuit Design](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=9531733)  
2. [Instructables - ECG Circuit](https://www.instructables.com/Electrocardiogram-ECG-Circuit/)  
3. [Instructables - ECG Circuit (Part 2)](https://www.instructables.com/Electrocardiogram-ECG-Circuit-2/)  
4. [Instructables - ECG Circuit (Part 3)](https://www.instructables.com/Electrocardiogram-ECG-Circuit-3/)

---

## 9. Contributors

- Pranav Maruti Shanbhag (USN: 4NI24EC407)  
- Adithya Y (USN: 4N23EC005)  
- Anirudha Jayaprakash (USN: 4NI23EC014)  
- Ballambettu Milan Shankar Bhat (USN: 4NI23EC019)  
- Aneesh R Kulkarni (USN: 4NI23EC013)  

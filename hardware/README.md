# Hardware Design – ECG Acquisition System

## 📌 Overview

This project uses a dedicated analog ECG front-end sensor interfaced with an **STM32F446RE** microcontroller to acquire and digitize cardiac electrical signals safely and reliably.

The hardware design focuses on **signal integrity, patient safety, and noise reduction**, which are critical in biomedical signal acquisition.

---

## 🧩 Major Hardware Components

### 1️⃣ ECG Analog Front-End

* **Sensor:** AD8386 ECG Analog Front-End
* Purpose:

  * Amplifies low-amplitude ECG signals (µV–mV range)
  * Filters motion artifacts and high-frequency noise
  * Provides conditioned analog output suitable for MCU ADC

---

### 2️⃣ Microcontroller Unit (MCU)

* **MCU:** STM32F446RE
* Role:

  * Samples ECG signal using internal ADC
  * Performs real-time signal validation
  * Handles AI inference and alert logic
  * Ensures deterministic timing and safety behavior

---

### 3️⃣ Power Supply

* **Operating Voltage:** 3.3V
* Regulated supply used for both MCU and ECG front-end
* Proper decoupling capacitors used near sensor and MCU pins
* Common ground reference maintained to avoid signal distortion

---

## 🔌 ECG Electrode Configuration

### Electrode Placement

* **RA (Right Arm / upper chest near right shoulder)**
* **LA (Left Arm / upper chest near left shoulder)**
* **RL (Right Leg / lower torso / reference ground)**

The RL electrode is used as a reference to:

* Reduce common-mode interference
* Improve signal stability
* Suppress power-line noise (50/60 Hz)
  
  <img width="460" height="404" alt="image" src="https://github.com/user-attachments/assets/fc65f706-23da-4ed1-84bb-fa90393aae44" />
  <img width="460" height="600" alt="image" src="https://github.com/user-attachments/assets/2295126f-3e0c-4e5d-b03d-477c0683a2a8" />



---

## 📈 Signal Flow

```
ECG Electrodes
      ↓
ECG Analog Front-End (AD8232 / AD8386)
      ↓
Analog ECG Signal
      ↓
STM32F446RE Microcontroller
 ┌─────────────────────────────────┐
 │  • Timer Configuration (250 Hz) │
 │  • ADC Acquisition              │
 │  • Digital Filtering            │
 │  • Signal Quality Check         │
 │  • Feature Extraction           │
 │  • Edge AI Classification       │
 │  • Alert & Decision Logic       │
 └─────────────────────────────────┘
      ↓
Display / Output Interface
(LCD / Serial / Logging)

```

---
<img width="768" height="512" alt="ChatGPT Image Jan 17, 2026, 12_42_50 AM" src="https://github.com/user-attachments/assets/75d8070e-bbb2-4d46-ba88-ae391b4561f7" />



## ⚙️ ADC Configuration Summary

* **Resolution:** 12-bit
* **Input Channel:** Single-channel ECG input
* **Sampling Rate:** 250 Hz (medical-standard ECG rate)
* **Sampling Method:** Timer-based, deterministic
* **Alignment:** Right-aligned ADC data

---

## 🛡️ Noise and Safety Considerations

* Short electrode leads to reduce motion artifacts
* Proper grounding to avoid floating inputs
* Input protection handled at sensor level
* Software-based signal-quality checks before AI processing

---

## 📌 Design Philosophy

* Hardware acts as a **real-time safety layer**
* AI is applied only to **validated ECG signals**
* System designed for **screening**, not diagnosis
* Emphasis on reliability over aggressive amplification

---

## 🖼️ Diagrams

This folder contains:

* System block diagram
* ECG electrode placement reference
* Sensor-to-MCU connection diagrams

(Refer to uploaded images in this directory)

---

## ⚠️ Disclaimer

This hardware design is intended **only for academic and research purposes**
and must not be used in clinical or medical environments.

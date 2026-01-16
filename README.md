# STM32-Based ECG Machine with Edge AI Capabilities

## 📌 Project Overview

This project is a **real-time embedded ECG monitoring system** built using an **STM32F446RE microcontroller** and an analog ECG front-end sensor.
The system acquires ECG signals, performs signal-quality checks, and applies **Edge AI–based classification** to detect common cardiac rhythm abnormalities.

The design follows a **screening (not diagnostic)** approach, focusing on reliability, explainability, and real-time safety at the embedded level.

---

## 🎯 Objectives

* Acquire clean ECG signals in real time using an embedded system
* Process ECG data safely and deterministically on an STM32 MCU
* Detect common heart rhythm abnormalities using AI-assisted logic
* Provide confidence-aware and explainable alerts
* Demonstrate strong integration of **hardware, firmware, and AI**

---

## 🧠 Detected Cardiac Conditions

The system classifies ECG signals into the following categories:

* **Normal Heart Rhythm (Normal Sinus Rhythm)**
* **Bradycardia** (Slow Heart Rate)
* **Tachycardia** (Fast Heart Rate)
* **Premature Ventricular Contraction (PVC)**
* **Atrial Fibrillation (AF)** – Basic Detection
* **Missed Beat / Pause**

---

## 🛠️ System Components

### Hardware

* **Microcontroller:** STM32F446RE
* **ECG Sensor:** AD8386 (Analog Front-End)
* **ADC Resolution:** 12-bit
* **Sampling Rate:** 250 Hz (medical-standard ECG rate)

### Firmware

* Bare-metal firmware (no RTOS)
* Timer-based deterministic ECG sampling
* Signal-quality validation before AI processing
* Clear separation between safety-critical acquisition and AI logic

### AI / Edge Intelligence

* AI model trained offline using Python
* Feature-based ECG segment analysis
* Confidence score generated for each prediction
* Explainable alert logic (reason logging)

---

## 🧩 Key Features

* Real-time ECG acquisition on STM32
* Noise-aware signal gating before inference
* Edge AI classification suitable for low-power systems
* Two-level alert system (Warning / Critical)
* Patient-adaptive baseline learning
* Trend-based abnormality detection over time
* Designed with embedded safety and explainability in mind

---

## 📊 Project Structure

```
STM32-based-ECG-Machine-with-EdgeAI-capabilities/
├── hardware/        # Circuit diagrams, sensor connections
├── firmware/        # STM32 firmware source
├── ai_model/        # AI training and evaluation code
├── docs/            # System architecture and design notes
└── results/         # ECG plots and classification outputs
```

---

## ⚠️ Disclaimer

This project is intended **for academic and screening purposes only**.
It is **not a medical diagnostic device** and should not be used for clinical diagnosis or treatment.

---

## 📌 Skills Demonstrated

* Embedded C and STM32 firmware design
* ADC configuration and real-time signal acquisition
* Biomedical signal handling
* Edge AI integration on resource-constrained systems
* System-level engineering and documentation

---

## 🔗 Author

Developed as a final-year engineering project focusing on **embedded systems, biomedical instrumentation, and edge AI**.

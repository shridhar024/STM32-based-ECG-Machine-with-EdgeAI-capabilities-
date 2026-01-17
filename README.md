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

## 🔗 Author ( Shridhar Mangsule)

Developed as a final-year engineering project focusing on **embedded systems, biomedical instrumentation, and edge AI**.







# 📌 Project Progress Details

### ✅ Completed Work

* Studied and understood ECG signal fundamentals, including P–QRS–T waveform and RR-interval interpretation
* Developed clear understanding of how ECG timing patterns relate to heart rhythm abnormalities
* Set up SWV (Single Wire Viewer) debugging environment for real-time embedded debugging
* Configured ITM (Instrumentation Trace Macrocell) console for data output
* Successfully plotted real-time ECG signals on PC **without using UART**, using ITM-based debugging
* Implemented reliable ECG signal acquisition on STM32 microcontroller
* Designed and implemented baseline wander removal using a digital low-pass filtering approach
* Verified improvement in ECG signal stability and baseline correction after filtering
* Converted MIT-BIH ECG dataset into CSV format for machine learning workflows
* Initiated exploration and experimentation with 1D CNN deep learning models for ECG classification

---

### ⏳ Planned Work / Future Scope

#### 🔧 Firmware Enhancements

* Improve robustness of R-peak detection under noise and motion artifacts
* Implement adaptive thresholding for more reliable R-peak detection
* Refine signal quality validation to detect lead-off, saturation, and abnormal conditions
* Optimize firmware execution timing and memory usage
* Perform long-duration continuous ECG monitoring tests for stability

---

#### 📊 Signal Processing Improvements

* Implement band-pass filtering to better isolate QRS complex
* Evaluate derivative-based and moving-average techniques for peak detection
* Improve baseline wander correction under varying electrode and motion conditions
* Perform RR-interval trend analysis over extended time windows

---

#### 🤖 AI / Machine Learning Development

* Complete preprocessing pipeline for MIT-BIH ECG dataset
* Organize, label, and balance ECG classes for training
* Finalize lightweight 1D CNN architecture suitable for ECG time-series data
* Train and validate the model using standard performance metrics
* Compare AI-based classification with RR-interval–based rule detection
* Optimize model size and inference complexity for embedded deployment

---

#### 🧠 Hybrid Decision Logic

* Combine rule-based RR-interval detection with AI model outputs
* Introduce confidence-based decision thresholds
* Reduce false positives through temporal smoothing and trend analysis
* Implement explainable alert logic based on detected signal features

---

#### 📈 Results & Validation

* Generate ECG waveform plots before and after filtering
* Document RR-interval patterns for each detected condition
* Perform repeatability testing across multiple ECG recordings
* Summarize observed detection behavior and limitations

---

#### 🧪 Testing & Reliability

* Conduct extended runtime testing of firmware
* Validate timing accuracy of timer-driven ADC sampling
* Measure CPU utilization during signal processing and AI inference
* Test system behavior under varying noise and signal conditions

---

#### 🎯 Final Objective

To deliver a **reliable, well-documented, and safety-aware embedded ECG screening system** that demonstrates strong understanding of biomedical signals, real-time embedded system design, and responsible Edge AI integration.

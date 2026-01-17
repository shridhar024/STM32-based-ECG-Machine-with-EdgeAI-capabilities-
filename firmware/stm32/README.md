# STM32 Firmware Design – ECG Acquisition and Processing

## 📌 Overview

The firmware for this project is implemented on an **STM32F446RE** microcontroller using a **bare-metal (no RTOS)** approach.
The design focuses on **deterministic timing, reliability, and safety**, which are critical for biomedical signal acquisition like ECG.

The STM32 acts as a **real-time safety and acquisition layer**, while AI logic operates only on validated ECG data.

---

## 🧠 Design Philosophy

* **Bare-metal implementation** for predictable timing
* **Timer-driven sampling** instead of polling
* Clear separation between:

  * Signal acquisition
  * Signal processing
  * Decision & alert logic
* AI is used as an **assistive layer**, not a real-time controller

---

## ⚙️ System Configuration

### Microcontroller

* **MCU:** STM32F446RE
* **System Clock:** 84 MHz
* **Programming Environment:** STM32CubeIDE
* **Language:** Embedded C

---

## ⏱️ Timer-Based Sampling

* A hardware timer is configured to generate a **250 Hz sampling trigger**
* This ensures:

  * Uniform ECG sampling interval
  * Medical-standard ECG timing
  * Deterministic execution independent of main loop delays

**Why Timer-Based Sampling?**

* Avoids jitter caused by software delays
* Ensures consistent RR-interval measurement
* Suitable for long-duration monitoring

---

## 🔢 ADC Configuration

* **Resolution:** 12-bit
* **Mode:** Single-channel conversion
* **Sampling Time:** Long sampling time to reduce noise
* **Data Alignment:** Right-aligned
* **Trigger Source:** Timer-controlled (software synchronized)

The ADC digitizes the conditioned analog ECG signal from the ECG front-end.

---

## 🔄 Firmware Execution Flow

```
System Initialization
      ↓
Clock & Peripheral Setup
      ↓
Timer Configuration (250 Hz)
      ↓
ADC Configuration
      ↓
Main Loop Execution
      ↓
• Wait for sampling trigger
• Acquire ECG sample
• Apply digital filtering
• Validate signal quality
• Extract ECG features
• Perform AI-based classification
• Generate alerts/output
```

---

## 🧮 Digital Signal Processing

Basic digital processing is applied to improve ECG signal quality:

* Baseline wander reduction
* High-frequency noise suppression
* Simple smoothing for motion artifact reduction

Filtering is intentionally lightweight to maintain real-time performance.

---

## ✅ Signal Quality Validation

Before AI inference, the firmware checks:

* Signal saturation
* Sudden amplitude spikes
* Flat-line or lead-off conditions

If signal quality is poor:

* AI inference is skipped
* Output is marked as unreliable
* System continues monitoring

---

## 🧠 Feature Extraction

Extracted ECG features include:

* Heart rate estimation
* RR-interval calculation
* Beat presence and timing
* Pause / missed beat detection

These features form the input to the Edge AI logic.

---

## 🤖 Edge AI Integration

* AI model is trained offline
* Lightweight inference logic used on STM32
* Each prediction includes a **confidence score**
* AI output is combined with rule-based logic for safety

Detected classes include:

* Normal rhythm
* Bradycardia
* Tachycardia
* PVC
* Atrial Fibrillation (basic)
* Missed beat / pause

---

## 🚨 Alert & Decision Logic

* Two-level alert system:

  * **Warning**
  * **Critical**
* Alerts are triggered based on:

  * AI output
  * Threshold-based conditions
  * Trend analysis over time

This hybrid approach improves reliability.

---

## 🧪 Why No RTOS?

* ECG sampling requires strict timing guarantees
* System complexity is moderate and manageable without tasks
* Bare-metal design:

  * Reduces overhead
  * Simplifies debugging
  * Improves determinism

RTOS may be explored in future extensions but is intentionally avoided here.

---

## 📌 Key Takeaways

* Deterministic timer-driven design
* Strong focus on safety and signal validity
* Clear separation of concerns
* Embedded-first approach to Edge AI

---


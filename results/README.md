# Results and Observations

## 📌 Overview

This section summarizes the observed behavior and outcomes of the STM32-based ECG machine during development and testing.

The focus is on **system stability, signal quality, and correct detection logic**, rather than clinical accuracy.

---

## 📈 ECG Signal Acquisition

* Stable ECG waveform successfully acquired using analog ECG front-end
* Sampling maintained at **250 Hz** using timer-based triggering
* ADC readings showed consistent resolution and minimal jitter
* Baseline drift and high-frequency noise reduced through digital filtering

---

## 🧠 Rhythm Detection Behavior

The system was able to identify and differentiate the following conditions during testing:

* Normal sinus rhythm under steady conditions
* Bradycardia and tachycardia based on heart rate thresholds
* Premature Ventricular Contractions (PVC) through irregular beat timing
* Missed beats / pauses detected via extended RR intervals
* Basic atrial fibrillation patterns using rhythm irregularity metrics

---

## 🤖 AI-Assisted Classification

* AI inference executed only on validated ECG segments
* Confidence score generated for each classification
* Low-confidence predictions handled conservatively
* Hybrid rule-based + AI logic improved robustness

---

## ⚙️ System Reliability

* Deterministic timing maintained without RTOS
* No sampling overruns observed during continuous operation
* Firmware remained stable over extended runtime tests

---

## ⚠️ Notes

* Results are for academic and screening demonstration purposes
* Performance depends heavily on signal quality and electrode placement
* Further dataset expansion would improve AI generalization

---

## ✅ Conclusion

The project successfully demonstrates a **reliable, timer-driven embedded ECG system** with responsible Edge AI integration, suitable for academic and research use.

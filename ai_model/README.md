# Edge AI Design – ECG Abnormality Detection

## 📌 Overview

This project integrates **Edge AI** with an embedded ECG acquisition system to assist in the detection of common cardiac rhythm abnormalities.
The AI component is designed to operate under **resource constraints** and is used strictly as a **screening aid**, not a diagnostic tool.

All models are trained **offline** and deployed in a lightweight form suitable for embedded execution.

---

## 🧠 Design Philosophy

* AI is **assistive**, not authoritative
* Safety and signal validity take priority over predictions
* Prefer explainability over complex black-box models
* Edge constraints guide model choice and complexity

---

## 📊 Input Data

* **Input Signal:** Digitized ECG waveform
* **Sampling Rate:** 250 Hz
* **Segment Length:** Fixed-length ECG windows
* **Precondition:** Signal quality must be validated before AI processing

Poor-quality or noisy signals are **rejected before inference**.

---

## 🧮 Preprocessing

Before inference, ECG data undergoes:

* Baseline wander removal
* Noise smoothing
* Normalization
* Segmentation into analysis windows

Preprocessing is kept minimal to preserve real-time performance.

---

## 🧩 Feature Extraction

Instead of raw waveform inference, the system extracts interpretable features such as:

* Heart rate
* RR interval statistics
* Beat timing patterns
* Pause duration
* Rhythm regularity indicators

These features are used as inputs to the classification logic.

---

## 🤖 Model Approach

* **Training Environment:** Python
* **Model Type:** 1D CNN
* **Training Data:** Public ECG datasets (e.g., MIT-BIH, processed)
* **Deployment Target:** STM32 embedded system

The model is optimized for:

* Low memory usage
* Low computational overhead
* Stable inference timing

---

## 🏷️ Detected Classes

The AI-assisted system identifies the following rhythm conditions:

* Normal Sinus Rhythm
* Bradycardia
* Tachycardia
* Premature Ventricular Contraction (PVC)
* Atrial Fibrillation (Basic Detection)
* Missed Beat / Pause

---

## 📈 Confidence Scoring

Each prediction includes a **confidence score**, allowing:

* Safer alert generation
* Reduced false positives
* Transparent decision-making

Low-confidence predictions are treated conservatively.

---

## 🔄 Hybrid Decision Logic

AI outputs are combined with:

* Threshold-based rules
* Temporal trend analysis
* Heart-rate consistency checks

This hybrid approach improves robustness and reduces AI-only failures.

---

## 🚨 Output & Alerts

* AI results are forwarded to firmware decision logic
* Alerts are categorized as:

  * Warning
  * Critical
* All alerts are explainable and traceable to signal features

---

## ⚠️ Limitations

* Not a diagnostic-grade AI system
* AF detection is basic and screening-level
* Performance depends on signal quality and electrode placement
* Designed for educational and research use

---

## 📌 Key Takeaways

* Responsible use of AI in embedded systems
* Clear separation between acquisition, processing, and inference
* Edge-aware model design
* Safety-first decision strategy

---



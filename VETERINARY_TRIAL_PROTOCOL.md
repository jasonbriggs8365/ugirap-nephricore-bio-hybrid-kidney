# Pre-Clinical Veterinary In-Vivo Trial Protocol

**Project:** UGIRAP NephraCore™ Bio-Hybrid Wearable Kidney  
**Target Subjects:** Companion Feline & Canine Patients with IRIS Stage 3/4 CKD  
**Framework:** Open-Research Translational Protocol  

---

## 1. Objective & Hypothesis
* **Objective:** Validate continuous ambulatory hemoperfusion and dialysate regeneration via photoelectrocatalytic (PEC) urea sublimation in companion animal models.
* **Hypothesis:** Continuous low-volume (250–500 mL) closed-loop peritoneal sorbent circulation will maintain stable serum urea nitrogen (BUN < 40 mg/dL) and creatinine (< 2.5 mg/dL) over a 30-day wear period without requiring systemic anticoagulation.

---

## 2. Micro-Cartridge Veterinary Specifications
* **Recirculating Volume:** 250–500 mL biocompatible dialysate loop.
* **Membrane Architecture:** 150 cm² Silicon Nanopore Membrane (SNM) arrays with zwitterionic poly(sulfobetaine methacrylate) (pSBMA) hydrogel surface modification.
* **Urea Decomposition:** Pulsed 460 nm micro-LED photoelectrocatalytic array converting urea into inert N2 and CO2 gases.
* **Gas Venting:** Hydrophobic PTFE membrane manifold for ambient gas dispersion.

---

## 3. Sensor & Telemetry Integration
* **Dermal Sentinel Patch:** 3 cm x 2 cm micro-setae bio-adhesive patch.
* **Target Analytes:** Continuous interstitial fluid tracking of Potassium ($K^+$), Urea, and pH.
* **Safety Limits:** Automated pump throttles and safety shutdown executed via bare-metal `ce_os-kernel` logic if pH drops below 7.20 or $K^+$ exceeds 6.0 mmol/L.

---

## 4. Primary Endpoints & Regulatory Purpose
1. **Primary Endpoints:**
   * Sustained reduction of blood urea nitrogen (BUN) and serum creatinine.
   * Zero peritoneal membrane tissue inflammation or fibrotic response over 30 days.
   * Zero occurrence of thrombosis without systemic heparin administration.
2. **Regulatory Purpose:**
   * High-fidelity mammalian data collected under institutional veterinary oversight will directly support **FDA 21 CFR 312.300 (Expanded Access / Compassionate Use)** petitions for terminally ill human ESRD patients.

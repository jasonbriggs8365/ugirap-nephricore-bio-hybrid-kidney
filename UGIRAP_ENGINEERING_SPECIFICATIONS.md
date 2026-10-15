# UGIRAP: Universal Gas-Ion Regenerative Artificial Perfusion Platform
## Master Engineering & Physical Build Specifications

**Document Version:** 1.0  
**Project Repository:** `jasonbriggs8365/ugirap-nephricore-bio-hybrid-kidney`  
**Classification:** Open-Hardware Bio-Hybrid Medical Device Specification  

---

## 1. Executive Summary & Core Definition
The **UGIRAP** (Universal Gas-Ion Regenerative Artificial Perfusion) system is the foundational physical and fluidic infrastructure powering the NephraCore bio-hybrid kidney. It functions as an ambulatory, closed-loop extracorporeal and peritoneal purification unit that continuously cleanses, balances, and regenerates biological fluid matrices without requiring permanent municipal water hookups or large stationary clinical dialyzers.

---

## 2. Mechanical Housing & Structural Enclosure

### 2.1 Chassis Geometry & Materials
* **Primary Frame:** Injection-molded or 5-axis CNC-machined Medical-Grade PEEK (Polyether ether ketone) for ultimate chemical resistance, biocompatibility, and high tensile strength-to-weight ratio.
* **Internal Chassis Sealing:** Dual-channel fluoroelastomer (FKM) O-ring gasketing ensuring hermetic and waterproof (IP68) isolation of electronics from fluid paths.
* **Total Dimensions:** 220 mm × 160 mm × 85 mm.
* **Dry Weight:** 1.15 kg; Operating Weight (with active fluid volume): 1.55 kg.

### 2.2 Thermal Management
* **Passive Dissipation:** Integrated micro-fin heat sinks machined directly into the rear PEEK housing utilizing internal thermal transfer pads.
* **Active Control:** Low-profile thermoelectric Peltier junction coupled with internal temperature telemetry to maintain fluid matrix equilibrium at $37.0^\circ\text{C} \pm 0.5^\circ\text{C}$.

---

## 3. Fluidic Manifold & Pumping Architecture

### 3.1 Pumping Sub-System
* **Actuation Mechanism:** Dual opposite-phase micro-diaphragm piezo pumps.
* **Flow Rate Range:** Variable programmable flow from 15 mL/min to 80 mL/min.
* **Pulsatility:** Engineered 1.2 Hz pulse modulation to mimic natural physiological vascular compliance and prevent boundary-layer stagnation across membranes.

### 3.2 Tubing & Connectors
* **Internal Fluid Lines:** Platinum-cured medical-grade silicone tubing (Shore A 50, ID 3.2 mm, OD 6.4 mm).
* **Fittings & Manifolds:** Quick-release medical aseptic quick-disconnect couplings constructed from PVDF (Polyvinylidene fluoride).

---

## 4. Transducer & Piezo-Acoustic Integration

### 4.1 Ultrasonic Cavitation & Cellular Stimulation
* **Transducer Array:** High-frequency piezoceramic ring transducers (PZT-5H material) bonded to the exterior base of the primary fluid mixing chamber.
* **Operating Frequency:** 40 kHz continuous / 1 MHz pulsed intermittent cleaning sweeps.
* **Purpose:** Prevents protein fouling on membrane surfaces, enhances molecular diffusion across biological interfaces, and drives localized fluid mixing at the cellular level.

---

## 5. Power Management & Electrical Architecture

### 5.1 Power Supply
* **Primary Battery:** 14.8V rechargeable lithium-iron-phosphate (LiFePO4) battery pack (3400 mAh), chosen for thermal stability and high discharge safety profiles.
* **Power Regulation:** Isolated DC-DC switching regulators providing clean, low-ripple rails for analog sensor front-ends (3.3V) and actuator drivers (12V).

### 5.2 Processing Unit
* **MCU Board:** Custom 4-layer printed circuit board (PCB) featuring a RISC-V 32-bit dual-core processor running bare-metal `no_std` firmware (`ce_os-kernel`).
* **Communication Interface:** Dual-mode Bluetooth Low Energy (BLE 5.2) and encrypted serial debugging header.

---

## 6. Assembly & Manufacturing Workflow (Step-by-Step)

1. **Chassis Machining:** Mill the main PEEK housing and internal fluid channels to strict dimensional tolerances.
2. **Transducer Bonding:** Epoxy-bond PZT-5H piezoceramic transducers to the chamber floor using high-thermal-conductivity structural adhesive.
3. **Manifold & Valve Integration:** Install the platinum-cured silicone tubing lines, piezo diaphragm pumps, and check valves into the lower chassis tray.
4. **Electronics Installation:** Mount the 4-layer RISC-V PCB and battery pack into the isolated upper compartment, sealing with the FKM gasket.
5. **Sensor Calibration & Pressure Testing:** Perform a 24-hour pneumatic and hydrostatic pressure test at 300 mmHg to verify seal integrity before sterile fluid priming.

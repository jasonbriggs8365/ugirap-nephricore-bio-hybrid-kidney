Here is the complete engineering and assembly playbook formatted as markdown, ready to be added to your repository as BUILD_AND_ASSEMBLY_PLAYBOOK.md.
File Name: BUILD_AND_ASSEMBLY_PLAYBOOK.md
UGIRAP NephraCore™ Prototype Build & Assembly Playbook
Document Version: 1.0
Project Repository: jasonbriggs8365/ugirap-nephricore-bio-hybrid-kidney
Classification: Open-Hardware Prototype Manufacturing & Assembly Manual
License: MIT License
1. Safety & Cleanroom Prerequisites
 * Working Environment: Assembly of biological and blood/fluid contacting manifolds must occur inside an ISO Class 7 cleanroom or laminar flow hood.
 * Component Sterilization:
   * PEEK chassis and fluidic manifolds: Ethylene Oxide (EtO) sterilization.
   * MEMS Silicon Nanopore Membranes (SNM): Gamma irradiation (25\text{ kGy}).
   * Piezoceramic transducers and PCB assemblies: Isopropyl alcohol (70\%) surface disinfection.
2. Phase-by-Phase Assembly Playbook
Phase 1: Enclosure & Chassis Machining
 * Housing Fabrication: CNC-mill the main chassis from medical-grade Polyether ether ketone (PEEK) stock. Integrate fractal suture structural ribbing across internal walls to maximize crush resistance.
 * Gasket Sealing: Press-fit dual fluoroelastomer (FKM) O-rings into the perimeter sealing grooves around the lower chassis tray.
 * Peltier Thermal Plate: Mount the thermoelectric Peltier module to the rear chassis wall using thermally conductive adhesive. Connect micro-thermocouple leads to the analog sensor header.
Phase 2: Hemofiltration Cassette & Acoustic Transducer Mounting
 * SNM Inspection: Verify the 5–7 nm slit-pore grid under 100\times optical inspection. Confirm covalent grafting of the sub-5 nm zwitterionic pSBMA hydrogel monolayer.
 * Transducer Bonding: Epoxy-bond thin-film Aluminum Nitride (AlN) piezoceramic ring transducers directly to the outer Titanium cassette housing.
 * Cassette Sealing: Secure the SNM array into the cassette frame using FKM compression gaskets. Torque titanium assembly screws to 0.8\text{ Nm} in a cross-star pattern.
Phase 3: Photoelectrocatalytic (PEC) Reactor & Gas Venting Module
 * Photoanode Insertion: Install the nanostructured hematite (\alpha\text{-Fe}_2\text{O}_3) / NiOOH photoanode inside the quartz microfluidic flow cell.
 * LED Light Source: Position the 460 nm blue micro-LED array 2.0\text{ mm} above the photoanode window, delivering 25\text{ mW/cm}^2 continuous irradiance.
 * Degassing Manifold: Install the 0.2\,\mu\text{m} hydrophobic expanded polytetrafluoroethylene (PTFE) degassing membrane over the exhaust manifold to allow passive venting of evolved Nitrogen (N_2) and Carbon Dioxide (CO_2) gases.
Phase 4: Fluidic Plumbing & Micro-Pulsatile Pump Drive
 * Silicone Line Routing: Connect platinum-cured silicone tubing (3.2\text{ mm} inner diameter) between the fluid inlet, SNM hemofilter, PEC cell, and outlet manifolds.
 * Diaphragm Pump Installation: Mount the dual opposite-phase piezoceramic diaphragm pumps. Wire drivers to run in opposite-phase modulation (30\text{ to }60\text{ mL/min}) to minimize shear stress.
 * Aseptic Coupling: Attach PVDF quick-disconnect couplings to the external port mounts.
Phase 5: PCB Mounting, Telemetry & Firmware Deployment
 * PCB Installation: Secure the 4-layer RISC-V controller board into the upper isolated dry compartment.
 * Wiring Harness: Connect piezoceramic drivers, ISFET telemetry sensors (K^+, pH, temperature), and LED power rails to the controller header.
 * Firmware Flashing: Flash the bare-metal ce_os-kernel Rust binary (riscv32imac-unknown-none-elf) via the SWD debugging interface.
3. Benchtop Calibration & Acceptance Testingtext
[ Hydrostatic Test (300 mmHg) ] ──► [ Electrical & Sensor Calibration ] ──► [ 72-Hour Recirculation Run ]

### Protocol A: Hydrostatic Pressure & Leak Test
* Pressurize the fluid manifold with sterile isotonic saline to $300\text{ mmHg}$ for 30 minutes.
* **Pass Criteria:** Zero fluid pressure drop ($\Delta P = 0\text{ mmHg}$) and zero visual or electronic moisture detection across internal seals.

### Protocol B: Acoustic Defouling Sweep Verification
* Power on the AlN piezo transducers and initiate the $40\text{ kHz}$ DF-IPSS sweep cycle.
* **Pass Criteria:** Hydrophone mapping must confirm acoustic energy density remains strictly capped below $0.25\text{ W/cm}^2$.

### Protocol C: 72-Hour Benchtop Recirculation Run
* Recirculate synthetic uremic fluid ($BUN = 80\text{ mg/dL}$, Creatinine $= 10\text{ mg/dL}$) at $40\text{ mL/min}$.
* **Pass Criteria:**
  * Active urea gas conversion rate $\ge 0.4\text{ g/hour/100 cm}^2$ active photoanode area under 460 nm LED light.
  * Normalized hydraulic flux across the zwitterionic SNM drops by $< 5\%$ over 72 hours.
  * Deterministic safety firewall interrupts trigger in $< 1\text{ }\mu\text{s}$ upon simulated air bubble or pressure spike injection.

Optional Commit Description:
Added comprehensive step-by-step prototype manufacturing, assembly, and 72-hour benchtop testing playbook.

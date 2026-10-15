# UGIRAP NephraCore™: Standard Operating Procedures (SOP) for Assembly

**Document Version:** 1.0  
**Project Repository:** `jasonbriggs8365/ugirap-nephricore-bio-hybrid-kidney`  

---

## 1. Cleanroom & Sterilization Prerequisites
* **Assembly Environment:** ISO Class 7 (Class 10,000) cleanroom environment or sterile laminar flow hood.
* **Component Sterilization:** PEEK chassis components subjected to ethylene oxide (EtO) sterilization; silicon nanopore membranes (SNM) sterilized via gamma irradiation ($25\text{ kGy}$).

## 2. Step-by-Step Mechanical Integration SOP
1. **Housing Inspection:** Verify structural integrity and surface smoothness of the milled PEEK enclosure under 10x magnification.
2. **Transducer Array Mounting:** Apply thermally conductive epoxy to PZT-5H piezoceramic rings; cure under controlled $60^\circ\text{C}$ infrared heat for 2 hours.
3. **Membrane Sealing:** Install the zwitterionic pSBMA-coated Silicon Nanopore Membrane into the titanium core cassette using FKM fluoroelastomer compression gaskets. Torque fastening screws to $0.8\text{ Nm}$ in a star pattern.
4. **Firmware Flash:** Connect the RISC-V development header to the 4-layer PCB and flash the `ce_os-kernel` binary via secure SWD interface. Run automated hardware self-test suite (`cargo test --target riscv32imac-unknown-none-elf`).
5. **Hydrostatic Pressure Test:** Pressurize the fluid manifold with sterile saline at $300\text{ mmHg}$ for 30 minutes to verify zero micro-leaks prior to final packaging.

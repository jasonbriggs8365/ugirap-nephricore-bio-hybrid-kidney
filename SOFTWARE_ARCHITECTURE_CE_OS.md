# UGIRAP NephraCore™: Software Architecture & `ce_os` Kernel Specifications

**Document Version:** 1.0  
**Project Repository:** `jasonbriggs8365/ugirap-nephricore-bio-hybrid-kidney`  
**Classification:** Open-Source Embedded Firmware & Deterministic OS Architecture  

---

## 1. Operating System Overview (`ce_os`)
The **`ce_os`** (Cognitive Engine Operating System) is a deterministic, bare-metal operating system kernel written in memory-safe `no_std` Rust. It is custom-engineered for implantable and wearable bio-hybrid medical devices where execution timing, zero-allocation memory guarantees, and sub-millisecond safety interrupts are mandatory.

---

## 2. Core Architectural Principles
* **Zero Dynamic Allocation (`no_std`):** To prevent runtime memory fragmentation or heap exhaustion errors, all memory buffers, sensor queues, and state machines are statically allocated at compile time.
* **Deterministic Execution Loops:** Critical sensor polling and pump-actuation loops execute on hard real-time ticks (strictly bounded to $\le 5\,\text{ms}$ latency).
* **Fault-Isolation Boundaries:** The kernel separates high-level telemetry and Bluetooth (BLE) communication tasks from low-level safety-critical valve actuation and sensor monitoring.

---

## 3. Real-Time Safety Firewall & Interlocks
The kernel acts as an active hardware firewall. If any physiological or mechanical parameter breaches safe thresholds, `ce_os` overrides user settings and executes pre-programmed failsafes within microseconds:

1. **Potassium Breach ($K^+ > 6.2\text{ mmol/L}$):**
   * *Action:* Immediate throttle of dialysate recirculation pump; audio/haptic pulse alert triggered on dermal patch.
2. **Transmembrane Pressure (TMP) Spike ($> 220\text{ mmHg}$):**
   * *Action:* Instant valve bypass to isolate the patient loop and vent overpressure through the PTFE gas-separation manifold.
3. **pH Level Departure ($\text{pH} < 7.20$ or $> 7.60$):**
   * *Action:* Automatic adjustment of the buffer-injection micro-valve array to restore physiological acid-base equilibrium.

---

## 4. Firmware Directory Structure
When fully populated, the repository's `/firmware/` directory adheres to this embedded layout:

```text
/firmware/
├── ce_os-kernel/
│   ├── Cargo.toml               # Rust package manifest (no_std)
│   ├── src/
│   │   ├── main.rs              # System entry point & hardware boot strap
│   │   ├── scheduler.rs         # Hard real-time task scheduler
│   │   ├── safety_firewall.rs   # Threshold interrupt monitors & fail-safes
│   │   ├── drivers/             # Piezoceramic drivers & ISFET sensor readers
│   │   └── comms.rs             # Encrypted JSON packet streaming over BLE

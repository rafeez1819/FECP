# Sherin FECP – Forensic Evidence Collection Protocol
> Tamper‑punitive, zero‑trust evidence preservation on‑device.  
> Turns every physical attack into immutable, auditable forensic data while instantly rendering the compromised hardware inert.

---

## Table of Contents
1. [Why FECP?](#why-fecp)  
2. [Key Capabilities](#key-capabilities)  
3. [Architecture Overview](#architecture-overview)  
4. [Getting Started (dev / test)](#getting-started)  
5. [Running the Daemon](#running-the-daemon)  
6. [Testing & Validation](#testing--validation)  
7. [Compliance & Auditing](#compliance--auditing)  
8. [Contributing](#contributing)  
9. [License](#license)  
10. [Contact & Support](#contact--support)  

---

## Why FECP? <a name="why-fecp"></a>

Physical compromise of a device—hammer, fire, EMP, or covert tampering—has historically destroyed the forensic trail. In many regulated sectors (defence, health, finance, critical infrastructure) the loss of that trail makes investigations impossible and can cripple legal accountability.

**Sherin FECP** solves this by:

* **Detecting** unauthorized physical intrusion (accelerometer ≥ 50 g, temperature ≥ 85 °C, voltage anomaly, case‑open sensor, or 3 software‑strike events).  
* **Capturing** a cryptographically signed snapshot (GPS ± 5 m, full memory hash, sensor state) **within 1 ms** of detection.  
* **Broadcasting** the evidence on **five independent channels** (Cellular LTE‑M, Wi‑Fi, BLE‑mesh, Iridium Satellite, Ultrasonic).  
* **Irreversibly bricking** the device (OTP‑fuse burn, TPM master‑key zeroising, power‑shunt) to prevent reuse.  

All actions are performed **offline**, maintaining full privacy and security.

---

## Key Capabilities <a name="key-capabilities"></a>

| Capability | Technical Detail | Benefit |
|------------|-----------------|---------|
| **Three‑Strike Tamper Counter** | TPM 2.0 NVRAM monotonic counter; hardware‑fused OTP fuses | Guarantees destruction threshold is enforced. |
| **Immutable Evidence Ledger** | Ed25519‑signed snapshot roots in SHA‑256 Merkle tree | End-to-end verifiable evidence. |
| **DNA Vault (SHFS)** | AES‑256-GCM encrypted, 2-bit encoded, Reed-Solomon error correction | Forensic storage that survives power loss. |
| **Multi‑Channel Broadcast** | LTE‑M, Wi‑Fi, BLE mesh, Iridium, Ultrasonic | Resilient to RF or EMP interference. |
| **API‑First Evidence Access** | REST + WebSocket JSON-Web-Signature endpoints | Easy integration with SOC/SIEM tools. |
| **Policy‑Governed Logging** | Brick events controllable via signed supervisory commands | Meets legal oversight requirements. |
| **Post‑Quantum Ready** | Optional Kyber‑768 KEM path | Future-proof against quantum attacks. |

---

## Architecture Overview <a name="architecture-overview"></a>


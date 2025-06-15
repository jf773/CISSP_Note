# Chapter 9: Security Vulnerabilities, Threats, and Countermeasures

- [Shared Responsibility](#shared-responsibility)
- [Data Localization and Data Sovereignty](#data-localization-and-data-sovereignty)
- [Assess and Mitigate the Vulnerabilities of Security Architectures, Designs, and Solution Elements](#assess-and-mitigate-the-vulnerabilities-of-security-architectures-designs-and-solution-elements)
  - [Hardware](#hardware)
  - [Firmware](#firmware)
- [Client-Based Systems](#client-based-systems)
  - [Mobile Code](#mobile-code)
  - [Local Caches](#local-caches)
- [Server-Based Systems](#server-based-systems)
  - [Large-Scale Parallel Data Systems](#large-scale-parallel-data-systems)
  - [Grid Computing](#grid-computing)
  - [Peer to Peer](#peer-to-peer)
- [Industrial Control Systems](#industrial-control-systems)
- [Distributed Systems](#distributed-systems)
- [High-Performance Computing (HPC) Systems](#high-performance-computing-hpc-systems)
- [Real-Time Operating Systems](#real-time-operating-systems)
- [Internet of Things](#internet-of-things)
- [Edge and Fog Computing](#edge-and-fog-computing)
- [Embedded Devices & Cyber-Physical Systems](#embedded-devices--cyber-physical-systems)
  - [Static Systems](#static-systems)
  - [Cyber-Physical Systems](#cyber-physical-systems)
  - [Security Concerns of Embedded and Static Systems](#security-concerns-of-embedded-and-static-systems)
- [Microservices](#microservices)
- [Infrastructure as Code](#infrastructure-as-code)
- [Immutable Architecture](#immutable-architecture)
- [Virtualized Systems](#virtualized-systems)
  - [Virtual Software](#virtual-software)
  - [Virtualized Networking](#virtualized-networking)
  - [Software-Defined Everything](#software-defined-everything)
  - [Virtualization Security Management](#virtualization-security-management)
- [Containerization](#containerization)
- [Mobile Devices](#mobile-devices)
  - [Mobile Device Security Features](#mobile-device-security-features)
  - [Mobile Device Deployment Policies](#mobile-device-deployment-policies)
- [Essential Security Protection Mechanisms](#essential-security-protection-mechanisms)
  - [Process Isolation](#process-isolation)
  - [Hardware Segmentation](#hardware-segmentation)
  - [Root of Trust](#root-of-trust)
  - [System Security Policy](#system-security-policy)
- [Common Security Architecture Flaws and Issues](#common-security-architecture-flaws-and-issues)
  - [Covert Channels](#covert-channels)
  - [Attacks Based on Design or Coding Flaws](#attacks-based-on-design-or-coding-flaws)
  - [Rootkits](#rootkits)
  - [Incremental Attacks](#incremental-attacks)
- [Summary](#summary)

---
### Shared Responsibility
* **Cloud mantra:** provider secures *the* cloud; customer secures *in* the cloud.  
* Varies by service model (IaaS > PaaS > SaaS).  
* Contractual artifacts: CSPM reports, CSA CAIQ, FedRAMP ATO letters.  
* **Exam cue:** Identify mis-scoped duties (patching hypervisor ≠ tenant job).

---
### Data Localization and Data Sovereignty
* Laws (GDPR Art 3, POPIA, PDPA) dictate where data may rest/flow.  
* Controls: region-pinned buckets, geo-fenced keys (HSM-cluster per region), lawful-access reviews.  
* **Hot topic for multinational scenarios.**

---
## Assess & Mitigate  

### Hardware
| Threat | Vector | Mitigation |
|--------|--------|------------|
| **Side-channel** (Spectre, Meltdown) | Speculative execution | Micro-code, kernel page-table isolation |
| **Rowhammer** | Repeated RAM writes | ECC RAM, TRR, LPDDR4/5 |

### Firmware
* UEFI rootkits, BMC/iLO backdoors.  
* Signed updates, Secure Boot, measured boot (**TPM PCRs**), firmware SBOM.

---

## Client-Based Systems  

### Mobile Code
- Java, JavaScript, ActiveX, Flash → sandbox, CSP, code signing.

### Local Caches
- Browser, DNS, SSO tokens → poisoning & side-jacking; use *no-store*, cache-busting, TLS.

---

## Server-Based Systems  

### Large-Scale Parallel Data Systems
* Hadoop/Spark risk: unauth REST, mis-set ACLs.  
* Use **Kerberos, TLS, Ranger**, node segmentation.

### Grid Computing
* Federated volunteer nodes; sign work units, encrypt comms.

### Peer to Peer
* Threats: DDoS amplification, data leakage; fix via **whitelist peers, rate-limit**.

---

### Industrial Control Systems
* **SCADA, DCS, PLC**; legacy protocols (Modbus, DNP3) unauth’d.  
* ISA/IEC 62443 zoning, data diodes, passive monitoring (ICS-IDS).

---

### Distributed Systems
* CAP-theorem trade-offs; secure gRPC, clock integrity, service-mesh mTLS.  

---

### High-Performance Computing (HPC) Systems
* MPI job hijack, high-speed interconnect eavesdropping; InfiniBand VLANs, node-level SELinux.  

---

### Real-Time Operating Systems
* Deterministic timing > complex crypto; use lightweight algorithms, MPU, static analysis.

---

### Internet of Things
* Constrained devices, default creds, insecure OTA.  
* Controls: SBOM, secure element, MUD profiles, micro-segmentation.

---

### Edge and Fog Computing
* Push compute near data; threats = physical capture, rogue workload.  
* Zero-trust, slice isolation (5G), lightweight EDR.

---

## Embedded & Cyber-Physical Systems  

### Static Systems
* Fixed-function (ATM, kiosk). Patch difficulty → compensate with physical hardening, template rebuild.

### Cyber-Physical Systems
* Sensors+actuators; safety first. IEC 61508, NIST 800-82.

### Security Concerns of Embedded and Static Systems
* Hard-coded keys, JTAG ports, EEPROM dumps.  
* Mitigation: conformal coating, fuse bits, secure enclave.

---

### Microservices
* Small stateless units; issues: **API sprawl, broken authZ, secret leakage**.  
* Use OPA policies, short-lived JWT, service mesh.

---

### Infrastructure as Code
* Terraform/Ansible; risks = secrets in code, drift.  
* Guardrails: SAST, policy-as-code (OPA), secret vaults.

---

### Immutable Architecture
* Re-deploy not patch → eliminates drift, speeds rollback.  
* Requires CI/CD, image signing, blue-green canaries.

---

## Virtualized Systems  

### Virtual Software
* Hypervisor escape (VENOM); prefer Type-1, keep patch cadence.

### Virtualized Networking
* vSwitch/VXLAN; inspect via vTAP, enforce micro-segmentation.

### Software-Defined Everything
* SDN, SDS, SDC; protect controllers (RBAC, certs, MFA).

### Virtualization Security Management
* Harden vCenter/SCVMM, template VMs, secure snapshot chain.

---

### Containerization
* Risks: poisoned images, breakout (runC).  
* Controls: namespaces, seccomp, AppArmor/SELinux, signed images (Notary, cosign).

---

## Mobile Devices  

### Mobile Device Security Features
* Secure Element, biometric auth, FDE, sandbox, SafetyNet/Attestation.

### Mobile Device Deployment Policies
* BYOD, COPE, CYOD. Enforce via MDM/UEM, enterprise container, remote wipe.

---

## Essential Security Protection Mechanisms  

### Process Isolation
* Address space separation, ring protections, ASLR.

### Hardware Segmentation
* IOMMU (VT-d), SR-IOV, TPM PCRs.

### Root of Trust
* Hardware anchor → verifies firmware, OS chain.

### System Security Policy
* Formal MAC rulesets, multilevel labels, ABCS matrices.

---

## Common Security Architecture Flaws and Issues  

### Covert Channels
* Storage vs timing. Mitigate w/ noise, strict reference monitor, auditing.

### Attacks Based on Design or Coding Flaws
* Buffer overflow, integer wrap, race (TOCTOU). Counter: memory-safe lang, fuzzing, SAST.

### Rootkits
* Kernel-mode, firmware. Detect with offline baseline, IMA, trusted boot logs.

### Incremental Attacks
* “Salami slicing,” bit-flipping, Rowhammer; mitigated by boundary checks, ECC.

---

## Summary
- Modern stacks (cloud, edge, IoT, OT) widen the attack surface.  
- Map **shared-responsibility** & **data-sovereignty** to control selection.  
- Harden every layer: hardware → firmware → OS → container → microservice.  
- Core mechanisms = **isolation, segmentation, secure boot, IaC guardrails**.  
- Recognize covert channels, rootkits, and design-level flaws; employ defense-in-depth + continuous monitoring for mitigation.  
- Expect CISSP scenarios on *who owns what risk*, patch vs immutability, and safeguarding ICS / IoT environments.

# Chapter 8: Principles of Security Models, Design, and Capabilities

- [Secure Design Principles]()
  - [Objects and Subjects]()
  - [Closed and Open Systems]()
  - [Secure Defaults]()
  - [Fail Securely]()
  - [Keep It Simple and Small]()
  - [Zero-Trust]()
  - [Trust but Verify]()
  - [Privacy by Design]()
  - [Secure Access Service Edge (SASE)]()
- [Techniques for Ensuring CIA]()
  - [Confinement]()
  - [Bounds]()
  - [Isolation]()
  - [Access Controls]()
  - [Trust and Assurance]()
- [Understand the Fundamental Concepts of Security Models]()
  - [Trusted Computing Base]()
  - [State Machine Model]()
  - [Information Flow Model]()
  - [Noninterference Model]()
  - [Composition Theories]()
  - [Take-Grant Model]()
  - [Access Control Matrix]()
  - [Bell-LaPadula Model]()
  - [Biba Model]()
  - [Clark-Wilson Model]()
  - [Brewer and Nash Model]()
- [Select Controls Based on Systems Security Requirements]()
  - [Common Criteria]()
  - [Authorization to Operate]()
- [Understand Security Capabilities of Information Systems]()
  - [Memory Protection]()
  - [Virtualization]()
  - [Trusted Platform Module (TPM)]()
  - [Interfaces]()
  - [Fault Tolerance]()
  - [Encryption/Decryption]()
  - [Manage the Information System Life Cycle]()
- [Summary]()

## Secure Design Principles  

### Objects and Subjects  
- **Subject** = active entity (user, process). **Object** = passive resource (file, DB row).  
- Enforcement via **reference monitor** to mediate every access (1972 Anderson paper).

### Closed and Open Systems  
| Model | Features | CISSP Hint |
|-------|----------|------------|
| **Closed** | Proprietary, tight control | Security by obscurity ⛔️ |
| **Open** | Public specs, peer-reviewed | Preferred (Kerckhoffs) ✅ |

### Secure Defaults  
- *Default-deny* posture; require explicit allow (firewall, IAM).  
- Principle of **least privilege** & **least functionality** (CIS Controls v8).

### Fail Securely  
- On error → maintain confidentiality & integrity (bank safe locks shut).  
- Contrast **fail open** (availability prioritized; e.g., fire exits).

### Keep It Simple and Small  
- **KISS** & *economy of mechanism* → fewer bugs, easier validation.  
- Formal verification feasible only on concise TCB.

### Zero-Trust  
- *“Never trust, always verify.”*  
- Micro-segmentation, continuous authN, **explicit context** (device, user, data).

### Trust but Verify  
- Legacy maxim; today morphed into **zero-trust + continuous monitoring**.

### Privacy by Design  
- Embed GDPR principles from inception: data minimization, purpose limitation, DPIA.

### Secure Access Service Edge (SASE)  
- Cloud-delivered combo of **SD-WAN + security (CASB, SWG, ZTNA, FWaaS)**.  
- Reduces back-haul latency; subject of new CISSP questions.

---

## Techniques for Ensuring CIA  

| Technique | Purpose | Example |
|-----------|---------|---------|
| **Confinement** | Restrict code to subset of resources | Sandbox, chroot |
| **Bounds** | Limits of confinement (memory segment, container) | SELinux context |
| **Isolation** | Enforce bounds; prevent cross-talk | VM, process rings |
| **Access Controls** | DAC, MAC, RBAC, ABAC ensure proper subject/object pairing |
| **Trust & Assurance** | *Trust* = acceptance; *Assurance* = evidence (testing, formal proof). | EAL levels |

---

## Understand Fundamental Concepts of Security Models  

### Trusted Computing Base (TCB)  
- **Kernel + reference monitor + security enforcements**; must be **small & verifiable**.

### State Machine Model  
- Secure ⇒ *always* secure as system transitions states. Basis of Bell-LaPadula.

### Information Flow Model  
- Tracks data paths to prevent leakage (e.g., multilevel MLS).

### Noninterference Model  
- Lower-level subjects **cannot be influenced** by higher-level actions; prevents covert channels.

### Composition Theories  
- How combining secure components affects overall security (**cascade, feedback, hook-up**).

### Take-Grant Model  
- Graph-based; four rights (take, grant, create, remove). Exam Q: Can B *take* from A?

### Access Control Matrix  
- Table of subjects × objects; conceptual base for ACL & capability lists.

### Bell-LaPadula Model  
- **Confidentiality** MLS; *no read up, no write down* (simple-security & *-property).

### Biba Model  
- **Integrity** counterpart; *no write up, no read down*.

### Clark-Wilson Model  
- Commercial integrity; **well-formed transactions + separation of duty** (TP, CD, IVP).

### Brewer and Nash Model  
- “*Chinese Wall*” conflict-of-interest; dynamic labels.

---

## Select Controls Based on Systems Security Requirements  

### Common Criteria (ISO 15408)  
- **Protection Profile (PP)** → **Security Target (ST)** → evaluation.  
- **EAL 1-7**; higher = more assurance (EAL4 most common COTS).

### Authorization to Operate (ATO)  
- Formal **accreditation** (e.g., FedRAMP, RMF step 6).  
- Sign-off states residual risk acceptable.

---

## Understand Security Capabilities of Information Systems  

| Capability | Quick Facts | CISSP Tip |
|------------|-------------|-----------|
| **Memory Protection** | Segmentation, paging, ASLR, DEP | Stop buffer overflows |
| **Virtualization** | Type-1 hypervisor ring -1; VM escape risk | Shared responsibility |
| **Trusted Platform Module (TPM)** | Chip stores **Endorsement Key**, PCRs for Secure Boot | BitLocker, attestation |
| **Interfaces** | API, CLI, GUI → input validation, authZ | Prevent insecure API calls |
| **Fault Tolerance** | RAID, clustering, load-balancing | Availability in CIA |
| **Encryption/Decryption** | Hardware AES-NI, SSL offload | Identify best placement |
| **Manage IS Life Cycle** | **SDLC / NIST RMF** phases: concept → design → implement → O&M → disposal | Include security early |

---

## Summary  
CISSP Domain 3 expects you to:  
- Apply **secure-by-design principles** (least, fail-secure, zero-trust, SASE).  
- Distinguish key **formal security models** (Bell-LaPadula ≠ Biba ≠ Clark-Wilson) and where used.  
- Map **TCB / reference monitor / state machine concepts** to real OS & hypervisors.  
- Use **Common Criteria** and understand EALs when selecting and accrediting controls.  
Master these to answer scenario questions on model selection, control justification, and system-capability trade-offs.

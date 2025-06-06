# Chapter 1: Security Governance Through Principles and Policies

- [Security 101]()
- [Understand and Apply Security Concepts]()
  - [Confidentiality]()
  - [Integrity]()
  - [Availability]()
  - [DAD, Overprotection, Authenticity, Nonrepudiation, and AAA Services]()
  - [Protection Mechanisms]()
- [Security Boundaries]()
- [Evaluate and Apply Security Governance Principles]()
  - [Third-Party Governance]()
  - [Documentation Review]()
- [Manage the Security Function]()
  - [Alignment of Security Function to Business Strategy, Goals, Mission, and Objectives]()
  - [Organizational Processes]()
  - [Organizational Roles and Responsibilities]()
  - [Security Control Frameworks]()
  - [Due Diligence and Due Care]()
- [Security Policy, Standards, Procedures, and Guidelines]()
  - [Security Policies]()
  - [Security Standards, Baselines, and Guidelines]()
  - [Security Procedures]()
- [Threat Modeling]()
  - [Identifying Threats]()
  - [Determining and Diagramming Potential Attacks]()
  - [Performing Reduction Analysis]()
  - [Prioritization and Response]()
- [Supply Chain Risk Management]()
- [Summary]()

## Security 101  
**Core idea:** Information security protects business value by balancing risk reduction with cost and usability.  

**Key take-aways**  
- Security is a **business problem first, technical problem second**.  
- Goal: **reduce risk to an acceptable level**, not to zero.  
- Confidentiality, integrity, and availability must be considered together.

---

## Understand and Apply Security Concepts  

### Confidentiality  
- Prevents unauthorized *disclosure* of data.  
- Controls: encryption, ACLs, classification & handling, steganography.  
- Enforced by **need-to-know** and **least privilege**.

### Integrity  
- Preserves *accuracy and completeness*.  
- Controls: hashing, digital signatures, change-control, source auth.  
- Logical vs. physical integrity.

### Availability  
- Ensures *timely, reliable* access to systems/data.  
- Controls: redundancy, clustering, RAID, UPS/generators, DoS protection.  
- Metrics: **MTBF, MTTR, RTO, RPO**.

### DAD, Over-protection, Authenticity, Non-repudiation, AAA  
- **DAD (Disclosure–Alteration–Destruction)** = attacker’s CIA.  
- Over-protection = wasted cost & complexity.  
- **Authenticity** verifies genuineness (certificates).  
- **Non-repudiation** via digital signatures + secure logging.  
- **AAA**: Authentication ➔ Authorization ➔ Accounting.

### Protection Mechanisms  
- Control types: preventive, detective, corrective, deterrent, compensating.  
- Aim for **defense-in-depth** proportional to risk.

### Security Boundaries  
- Logical/physical demarcations (VLAN, DMZ, sandbox).  
- Limit attack surface; simplify monitoring & response.

---

## Evaluate and Apply Security Governance Principles  
**Core idea:** Governance aligns security action with leadership’s risk appetite and legal duties.  

**Key take-aways**  
- **Top-down** direction: board ➔ executives ➔ security program.  
- Use frameworks (ISO 27001, NIST CSF, COBIT, SABSA).  
- Demonstrate **due care** & **due diligence**.

### Third-Party Governance  
- Contracts, SLAs, audits, right-to-inspect, SBOMs.

### Documentation Review  
- Periodic policy/standard/procedure reviews prove compliance & relevance.

---

## Manage the Security Function  

### Alignment to Business Strategy  
- Map strategy to security scorecards/OKRs; tie KPIs to risk goals.

### Organizational Processes  
- Inject security gates into M&A, project lifecycles, change-management.

### Organizational Roles & Responsibilities  
- Data owner, steward/custodian, user, auditor, controller, processor, exec sponsor—each with explicit accountability.

### Security Control Frameworks  
- Provide control catalogues & maturity benchmarks.

### Due Diligence & Due Care  
- **Due care** = reasonable actions; **due diligence** = continuous verification; both defend against negligence claims.

---

## Security Policy, Standards, Procedures, Guidelines  
| Level | Purpose | Nature |
|-------|---------|--------|
| **Policy** | What & Why | High-level, mandatory |
| **Standard / Baseline** | What (minimums) | Mandatory, specific |
| **Procedure** | How | Step-by-step, mandatory |
| **Guideline** | How (best practice) | Discretionary |

---

## Threat Modeling  
**Core idea:** Identify, rate, and mitigate attacks before deployment.  

1. **Identify threats** (STRIDE, Kill Chain, CAPEC).  
2. **Diagram** data/process flows, trust boundaries.  
3. **Reduction analysis** on entry/exit points & privilege transitions.  
4. **Prioritize & respond** (avoid, transfer, mitigate, accept).

---

## Supply Chain Risk Management  
- Assess hardware, firmware, software, and service providers.  
- Mitigations: vetted suppliers, tamper-evident packaging, SBOM, continuous monitoring.  
- SolarWinds et al. highlight need for *continuous* assurance.

---

## Summary  
Security governance is the **strategic glue** binding technical controls to business value. Master:  

* **CIA triad**, AAA, authenticity, non-repudiation  
* Layered controls at defined **boundaries**  
* Policy → standard → procedure hierarchy  
* **Due care & diligence**, governance frameworks  
* **Threat modeling** and supply-chain vigilance  

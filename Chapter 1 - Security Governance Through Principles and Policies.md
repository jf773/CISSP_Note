# Chapter 1: Security Governance Through Principles and Policies

- [Security 101](#security-101)
- [Understand and Apply Security Concepts](#understand-and-apply-security-concepts)
  - [Confidentiality](#confidentiality)
  - [Integrity](#integrity)
  - [Availability](#availability)
  - [DAD, Overprotection, Authenticity, Nonrepudiation, and AAA Services](#dad-overprotection-authenticity-nonrepudiation-and-aaa-services)
  - [Protection Mechanisms](#protection-mechanisms)
- [Security Boundaries](#security-boundaries)
- [Evaluate and Apply Security Governance Principles](#evaluate-and-apply-security-governance-principles)
  - [Third-Party Governance](#third-party-governance)
  - [Documentation Review](#documentation-review)
- [Manage the Security Function](#manage-the-security-function)
  - [Alignment of Security Function to Business Strategy, Goals, Mission, and Objectives](#alignment-of-security-function-to-business-strategy-goals-mission-and-objectives)
  - [Organizational Processes](#organizational-processes)
  - [Organizational Roles and Responsibilities](#organizational-roles-and-responsibilities)
  - [Security Control Frameworks](#security-control-frameworks)
  - [Due Diligence and Due Care](#due-diligence-and-due-care)
- [Security Policy, Standards, Procedures, and Guidelines](#security-policy-standards-procedures-and-guidelines)
  - [Security Policies](#security-policies)
  - [Security Standards, Baselines, and Guidelines](#security-standards-baselines-and-guidelines)
  - [Security Procedures](#security-procedures)
- [Threat Modeling](#threat-modeling)
  - [Identifying Threats](#identifying-threats)
  - [Determining and Diagramming Potential Attacks](#determining-and-diagramming-potential-attacks)
  - [Performing Reduction Analysis](#performing-reduction-analysis)
  - [Prioritization and Response](#prioritization-and-response)
- [Supply Chain Risk Management](#supply-chain-risk-management)
- [Summary](#summary)


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

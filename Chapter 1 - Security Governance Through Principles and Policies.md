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

| Key Idea | CISSP Take-away |
|----------|-----------------|
| **Security = Business enabler** | Protects mission, objectives, reputation—not just IT. |
| **Three evaluation types** | *Risk Assessment* (assets + threats + vulns), *Vulnerability Assessment* (automated scans), *Pen Test* (human stress-test). |
| **Cost-effectiveness 💰** | Choose controls with greatest risk-reduction per dollar. |
| **Legal defensibility ⚖️** | Controls must stand up in court (due diligence / due care). |
| **Security is a journey** | Continuous monitoring, reassessment, improvement. |

## Understand and Apply Security Concepts  

### Confidentiality  
*Goal:* prevent **unauthorized disclosure**.  
*Controls:* encryption, access control lists (ACLs), strong authN, data classification, personnel training.  
*Key terms:* sensitivity, discretion, secrecy, privacy, seclusion, isolation.

### Integrity  
*Goal:* maintain **accuracy and trustworthiness** of data & systems.  
*Controls:* hashing, MAC/HMAC, digital signatures, version control, least privilege, input validation.  
*Threats:* malware, coding errors, unauthorized changes.

### Availability  
*Goal:* ensure **timely and reliable** access for authorized users.  
*Controls:* redundancy, clustering, backups, UPS/generators, DoS protection, capacity monitoring.  
*Dependence:* cannot be achieved if confidentiality or integrity are broken.

#### CIA vs DAD  
| Principle (CIA) | Opposite Failure (DAD) |
|-----------------|------------------------|
| **Confidentiality** | **Disclosure** |
| **Integrity** | **Alteration** |
| **Availability** | **Destruction / DoS** |

### DAD, Overprotection, Authenticity, Nonrepudiation, and AAA Services  

* **Overprotection:** Excessive controls on C or I may harm A (and vice-versa).  
* **Authenticity 🔏** – assurance data is genuine & from claimed source.  
* **Nonrepudiation 📜** – subjects cannot deny actions (digital signatures, logs).  

#### AAA = I + A + A + A + A 😉  
| Phase | What Happens | Mechanisms |
|-------|--------------|-----------|
| **Identification** | “Who am I?” | Username, smart-card ID |
| **Authentication** | “Prove it!” | Password, biometrics, MFA |
| **Authorization** | “What can I do?” | RBAC, ACL, ABAC |
| **Auditing** | “Record it.” | Event/log capture |
| **Accounting** | “Review & hold accountable.” | Log analysis, SIEM, reports |

### Protection Mechanisms  

| Mechanism | Quick Definition | Example in Practice |
|-----------|------------------|---------------------|
| **Defense-in-Depth** | Layered controls in *series* | Firewall ➔ IPS ➔ WAF ➔ DLP |
| **Defense-in-Breadth** | Vendor/tech diversity | Different AV engines at email vs endpoint |
| **Abstraction** | Group/role-based control | HR role assigned to all HR docs |
| **Data Hiding** | Conceal data from unauthorized view | Sensitive vars in kernel space; steganography |
| **Encryption** | Transform data for secrecy & integrity | AES, RSA, TLS |

### Quick-Reference Cheat Sheet 📝  

| Concept | 1-Line Memory Hook |
|---------|-------------------|
| CIA Triad | *C I A keeps data Safe* |
| Risk vs Vuln vs Threat | *Risk = A × T × V* |
| AAA full list | *ID → Auth → Authz → Audit → Account* |
| Overprotection | *Too much C or I kills A* |
| CRL latency issue | *Revoked cert not blocked until next CRL pull* |

### What the CISSP LOVES to Ask 🌟  
1. **Tie security to business drivers** (mission, legal liability, ROI).  
2. **Map scenarios to CIA failures** (identify disclosure vs alteration vs destruction).  
3. **Select strongest AAA element** given a use-case (e.g., multifactor beats password).  
4. **Calculate residual risk** after applying layered controls.  
5. **Spot overprotection traps** that harm availability or usability.

## Security Boundaries  

* **Definition:** Intersection line between areas with **different security requirements** (e.g., LAN ↔ Internet).  
* **Types:**  
  * **Logical boundaries** – VLANs, trust zones, classification levels.  
  * **Physical boundaries** – walls, fences, data-center cages.  
* **Control Principle:** Deploy mechanisms (firewalls, guards, ACLs) that regulate all traffic **across** the boundary.  
* **Policy Tip:** Clearly define where control starts/ends for **both** physical & logical perimeters; guard to the value of assets (avoid over-spend).

## Evaluate and Apply Security Governance Principles  

Security governance = **board-level oversight** that aligns security with mission, legal duties, and risk appetite.

### Third-Party Governance  
| Aspect | What to Know for CISSP |
|--------|-----------------------|
| **External oversight** | Mandated by laws, regs, contracts, licenses. Auditors verify compliance. |
| **Outsourcer control** | Vendors/SaaS/contractors must meet *your* security stance; include in SLAs. |
| **Assessment methods** | On-site audits, SOC 2 / ISO 27001 reports, penetration tests. |
| **Open document exchange** | Policies, risk assessments, and audit trails shared before field audit. |

### Documentation Review  
1. **Pre-audit phase** – Evaluate submitted policies, procedures, and evidence against standards (COBIT, NIST SP 800-53).  
2. **Gatekeeper:** Incomplete docs ⇒ delay on-site audit; sufficient docs ⇒ audit focuses on live compliance.  
3. **ATO impact:** Government environments may revoke **Authorization to Operate** if documentation or controls fail.  
4. **Goal:** Validate that business processes are practical, cost-effective, and reduce risk.

### Quick CISSP Memory Hooks 📝  
* **Boundary control mantra:** *“Define, defend, document.”*  
* **Third-party mantra:** *“Trust but verify with audits & contracts.”*  
* **Documentation review mantra:** *“Paper first, site second.”*  

## Manage the Security Function  

Security cannot be a “set-and-forget.” It is a **measurable, continuously improved business process** that must map to the organization’s mission and risk appetite.

### Alignment of Security Function to Business Strategy, Goals, Mission, and Objectives  

| Planning Tier | Time Horizon | Key Outputs | CISSP Trigger Question |
|---------------|--------------|-------------|------------------------|
| **Strategic** | 3-5 yrs | Security vision, funding model, risk appetite, *annual review* | “Which plan defines long-term security direction?” |
| **Tactical**  | ~12 mos | Projects, budgets, acquisitions, staffing | “Which doc maps projects to strategy?” |
| **Operational** | Days → Qtr | SOPs, runbooks, configurations, training schedules | “Where are step-by-step procedures defined?” |

* **Top-down model:** Board/CEO → CISO → Managers → Users (exam’s *correct* answer).  
* *Bottom-up* seen as a distractor—select it only when the question calls it out as a weakness.

### Organizational Processes  

* **Acquisitions / Mergers:** Embed security due diligence; assess inherited risks & integrate controls before Day 1.  
* **Divestitures / Off-boarding:** Sanitize media, revoke credentials, conduct exit interviews.  
* **Change Control:** Formal request → impact analysis → approval → testing → production (Chapter 16 details).  
* **Third-party assessments:**  
  1. On-site audit  
  2. Document exchange & review  
  3. Policy/process review  
  4. Independent SOC / ISO27001 reports  

### Organizational Roles and Responsibilities  

| Role | Primary Duty | Liability Note |
|------|--------------|----------------|
| **Senior Manager (Asset Owner)** | Ultimate risk acceptance & policy sign-off | **Due diligence/care rests here** |
| **CISO / CSO** | Translate business risk into security program; report to board/CEO | Requires autonomy |
| **Security Professional** | Design & implement controls, write policies | *Implementer* not decision-maker |
| **Custodian** | Day-to-day data protection, backups, patching | Executes policy directives |
| **User** | Follow policy, least privilege | Can be disciplined for violations |
| **Auditor** | Independent verification, produce compliance reports | Must remain objective |

### Security Control Frameworks  

| Framework | Focus | Common Use |
|-----------|-------|------------|
| **ISO/IEC 27001/2** | ISMS lifecycle | Global enterprises |
| **NIST SP 800-53 / RMF / CSF** | Catalog of controls, risk process | U.S. gov’t & contractors |
| **COBIT** | IT governance, value delivery | Audit, board reporting |
| **SABSA** | Business-driven security architecture | Large multi-national design |
| **PCI DSS** | Cardholder data protection (12 reqs) | Merchants & processors |
| **FedRAMP** | Cloud services for U.S. federal data | CSP authorization |
| **ITIL** | Service management best practice | Ops + change + incident |
| **CIS Benchmarks** | Secure configuration baselines | Hardening guides |
| **Specialized** (SWIFT, HIPAA, etc.) | Sector/tech specific | Critical infrastructure |

**6 Key Principles for the Governance and management of enterprise IT:**
- Provide Stakeholder Value
- Holistic Approach
- Dynamic Governance System
- Governance Distinct from Management
- Tailored to Enterprise Needs
- End-to-End Governance System

*Exam tip:* Questions often ask *“Which framework best maps IT goals to business value?”* → COBIT.

### Due Diligence and Due Care  

| Term | Simple Mnemonic | Exam Context |
|------|-----------------|--------------|
| **Due diligence** | *Plan & detect* | Management **establishes** policies, performs risk analysis, oversees metrics. |
| **Due care** | *Do & correct* | Organization **implements** controls and day-to-day safeguards. |

Failure to demonstrate both can equal **negligence** → executive liability.

> **Key takeaway:** Managing the security function means translating business strategy into layered plans, assigning clear roles, leveraging recognized frameworks, and proving prudent oversight through due diligence and due care.

## Security Policy, Standards, Procedures, and Guidelines  

Hierarchical documentation = the backbone of a repeatable security program.

| Tier | Purpose | Mandatory? | Key CISSP Cue |
|------|---------|------------|---------------|
| **Policy** | High-level *what* & *why* (scope, roles, acceptable risk) | ✅ Yes (approved by senior mgmt) | “Defines strategic direction” |
| **Standard** | Uniform *requirements* for tech/process | ✅ | “Same config everywhere” |
| **Baseline** | Minimum security for all like-systems | ✅ | “Non-compliant host pulled” |
| **Guideline** | Recommended *how*; flexible | ⬜ Optional | “Should/May wording” |
| **Procedure (SOP)** | Step-by-step *how-to* | ✅ | “Operational runbook” |

> **Exam Pitfall:** Policies tell you **what** must happen; procedures tell you **exactly how** to do it.

### Security Policies  
* Organizational, Issue-Specific, System-Specific variants.  
* Provide proof of **due diligence** → reduce liability.  
* Built top-down; require senior-management sign-off.

### Security Standards, Baselines, and Guidelines  
* **Standard** = compulsory control (e.g., all laptops use BitLocker).  
* **Baseline** = lowest acceptable config (CIS Benchmarks).  
* **Guideline** = best-practice advice; adapts to context.

### Security Procedures  
* Change-controlled documents; updated with tech changes.  
* Enforce consistency → “same actions, same outcome.”

## Threat Modeling  

| Stage | Output | Tools / Methods |
|-------|--------|-----------------|
| **Identify threats** | Threat list (STRIDE, PASTA, VAST) | Asset-, Attacker-, or Software-centric |
| **Diagram attacks** | Data-flow / trust-boundary map | DFD, architecture charts |
| **Reduction analysis** | Decomposed components; trust boundaries, data paths, privileged ops | “Break it down” |
| **Prioritize & respond** | Ranked risk list; mitigations | Probability✕Impact, Heat Map, **DREAD** |

| Dimension | **Defensive Approach (Proactive)** | **Adversarial Approach (Reactive)** |
|-----------|------------------------------------|-------------------------------------|
| **When?** | *Early* — requirements & design stages | *Post-build* — test, pilot, or production stages |
| **Mind-set** | “**Build security in**” — predict threats, embed controls | “**Break & hunt**” — assume flaws exist, seek & exploit them |
| **Activities** | • Architecture risk analysis<br>• Secure design patterns<br>• Input validation rules<br>• Security user stories in Agile<br>• DevSecOps tooling (SAST, IaC scanning) | • Ethical hacking & pen-tests<br>• Fuzz testing, red teaming<br>• Source-code review (SCA)<br>• Threat hunting for IoCs<br>• Patch / hardening plans |
| **Goal** | Eliminate vulnerabilities **before code ships**; cheaper fixes | Discover *unforeseen* vulnerabilities & exposures; validate defenses |
| **Cost & Impact** | Lower long-term cost; reduces rework | Higher fix cost but critical for zero-days & evolving threats |
| **Success Metrics** | • Fewer security bugs per sprint<br>• Compliance by design | • Mean-time-to-detect (MTTD)<br>• Reduced exploit window |
| **CISSP Exam Hook** | *Proactive* security is most cost-effective and preferred (“security by design”). | *Reactive* security complements proactive measures; required for continuous assurance once systems are live. |

### Identifying Threats  
* **STRIDE**: Spoofing, Tampering, Repudiation, Info disclosure, DoS, Elevation.  
* **PASTA**: 7-stage risk-centric method (DO → RAM).  
* **VAST**: Agile-friendly, scalable.

### Determining & Diagramming Potential Attacks  
* Draw components, label **trust boundaries**, data flows, entry points.  
* Consider logical, physical, and social attack vectors.

### Performing Reduction Analysis  
Break system into:  
1. Trust boundaries  
2. Data flows  
3. Entry points  
4. Privileged operations  
5. Security assumptions

### Prioritization and Response  
* **Risk matrix (heat map)** or **DREAD**—focus on High/High cells first.  
* Select countermeasures by **cost-benefit** and alignment to risk appetite.

## Supply Chain Risk Management  

* **Goal:** Assure every link (vendors, firmware, cloud, logistics) meets or exceeds org security.  
* **Controls:**  
  - Silicon **Root of Trust**  
  - **PUF** chips (device fingerprint)  
  - **SBOM** for software transparency  
  - Contractual **SLAs/SLRs**, third-party audits  
* **Attack types:** Counterfeits, hardware implants, malicious firmware.  
* Build **minimum security requirements** into RFPs and monitor continuously.

## Summary  

1. **Documentation hierarchy** (Policy → Procedure) delivers clarity, consistency, and legal defensibility.  
2. **Threat modeling** is continuous—identify, diagram, decompose, and rank threats before (and after) deployment.  
3. **Supply-chain risk** can subvert all other controls; implement technical roots of trust and contractual verification.  
4. Senior-management endorsement, measurable metrics, and due-diligence evidence are non-negotiable for CISSP success. 🚀

# Chapter 2: Personnel Security and Risk Management Concepts

- [Personnel Security Policies and Procedures](#personnel-security-policies-and-procedures)
  - [Job Descriptions and Responsibilities](#job-descriptions-and-responsibilities)
  - [Candidate Screening and Hiring](#candidate-screening-and-hiring)
  - [Onboarding: Employment Agreements and Policy-Driven Requirements](#onboarding-employment-agreements-and-policy-driven-requirements)
  - [Employee Oversight](#employee-oversight)
  - [Offboarding, Transfers, and Termination Processes](#offboarding-transfers-and-termination-processes)
  - [Vendor, Consultant, and Contractor Agreements and Controls](#vendor-consultant-and-contractor-agreements-and-controls)
- [Understand and Apply Risk Management Concepts](#understand-and-apply-risk-management-concepts)
  - [Risk Terminology and Concepts](#risk-terminology-and-concepts)
  - [Asset Valuation](#asset-valuation)
  - [Identify Threats and Vulnerabilities](#identify-threats-and-vulnerabilities)
  - [Risk Assessment/Analysis](#risk-assessment-analysis)
  - [Risk Responses](#risk-responses)
  - [Cybersecurity Insurance](#cybersecurity-insurance)
  - [Cost vs. Benefit of Security Controls](#cost-vs-benefit-of-security-controls)
  - [Countermeasure Selection and Implementation](#countermeasure-selection-and-implementation)
  - [Applicable Types of Controls](#applicable-types-of-controls)
  - [Security Control Assessment](#security-control-assessment)
  - [Monitoring and Measurement](#monitoring-and-measurement)
  - [Risk Reporting and Documentation](#risk-reporting-and-documentation)
  - [Continuous Improvement](#continuous-improvement)
  - [Legal Risk](#legal-risk)
  - [Risk Frameworks](#risk-frameworks)
- [Social Engineering](#social-engineering)
  - [Social Engineering Principles](#social-engineering-principles)
  - [Eliciting Information](#eliciting-information)
  - [Prepending](#prepending)
  - [Phishing](#phishing)
  - [Spear Phishing](#spear-phishing)
  - [Whaling](#whaling)
  - [Spam](#spam)
  - [Shoulder Surfing](#shoulder-surfing)
  - [Invoice Scams](#invoice-scams)
  - [Hoax](#hoax)
  - [Impersonation and Masquerading](#impersonation-and-masquerading)
  - [Tailgating and Piggybacking](#tailgating-and-piggybacking)
  - [Dumpster Diving](#dumpster-diving)
  - [Identity Fraud](#identity-fraud)
  - [Typosquatting](#typosquatting)
  - [Influence Campaigns](#influence-campaigns)
- [Establish and Maintain a Security Awareness, Education, and Training Program](#establish-and-maintain-a-security-awareness-education-and-training-program)
  - [Awareness](#awareness)
  - [Training](#training)
  - [Education](#education)
  - [Improvements](#improvements)
  - [Effectiveness Evaluation](#effectiveness-evaluation)
- [Summary](#summary)

## Personnel Security Policies and Procedures

Humans can be the weakest or strongest part of a security solution. This section explores policies and procedures designed to manage personnel effectively throughout the employment lifecycle.

### Job Descriptions and Responsibilities
- **Job Description**: Defines roles, duties, required access, and security requirements.
- **Security Consideration**: Access to classified or sensitive material must be explicitly stated.
- **Use in Governance**: Guides assignment of permissions and enforcement of least privilege.
- **Ongoing Use**: Regular audits ensure duties match access rights (avoiding privilege creep).

### Candidate Screening and Hiring
- **Screening Based on Role Sensitivity**: More sensitive roles require more intensive checks.
- **Elements**:
  - Work and education history
  - Reference checks
  - Criminal background checks
  - Identity verification (e.g., fingerprints)
  - Drug and personality tests (where applicable)
- **Online Background Check**: Review of applicant's public online presence—must be legally compliant.
- **Structured Interviewing**: Ensures fairness, legal defensibility.

### Onboarding: Employment Agreements and Policy-Driven Requirements
- **Onboarding Process**:
  - IAM system account creation
  - Privileges assigned per least privilege principle 🔐
  - Employee signs agreements: AUP, NDA, etc.
- **Employment Agreements**:
  - Job expectations, acceptable use, and penalties
- **Acceptable Use Policy (AUP)**:
  - Defines allowed/forbidden behaviors on systems
- **Non-Disclosure Agreement (NDA)**:
  - Legal contract preventing disclosure of confidential info (unilateral, bilateral, multilateral)
- **Non-Compete Agreement (NCA)**:
  - Restricts post-employment competition; enforceability varies by jurisdiction

### Employee Oversight
- **Job Review**:
  - Periodic audits of roles and access
  - Corrects privilege creep
- **Mandatory Vacations**:
  - Peer review and fraud detection method (esp. finance sector)
- **Separation of Duties / Job Rotation / Cross-Training**:
  - Prevents collusion and abuse of power
- **UEBA (User and Entity Behavior Analytics)**:
  - Behavior analysis of users and systems for anomaly detection

### Offboarding, Transfers, and Termination Processes
- **Offboarding Process**:
  - Identity and access removed via IAM
  - Certificates revoked, access disabled
- **Transfer = Offboard/Rehire** (if needed):
  - Especially when changing departments
- **Termination Procedures**:
  - Respectful but security-focused (e.g., escort, collection of assets)
  - Avoid early notification signs (e.g., locking account too soon)
- **Exit Interviews**:
  - Gain feedback and reinforce NDA
- **Best Practice**:
  - Notify all physical/logical access points

### Vendor, Consultant, and Contractor Agreements and Controls
- **SLAs (Service-Level Agreements)**:
  - Defines expectations, penalties, and security baselines
  - Used for ISPs, SaaS, databases, critical services
- **Multiparty Risk**:
  - Diverse timelines, goals, and security postures introduce risk
- **Outsourcing**:
  - Risk transference strategy, but introduces new risks
- **Trade Secret Theft Risk**:
  - Outsiders may not have same loyalty—monitor accordingly
- **VMS (Vendor Management System)**:
  - Tools to manage external entities securely, track interactions

### Comparison Table: NDA Types
| NDA Type     | Description                                     | Use Case                          |
|--------------|--------------------------------------------------|-----------------------------------|
| Unilateral   | One-way: only one party discloses information   | Employer to employee              |
| Bilateral    | Both parties share and protect information      | Two companies in partnership      |
| Multilateral | Three or more parties share mutual information  | Consortiums or multi-party deals  |

> 🧠 Treat people as security partners, not just liabilities. A strong personnel security program blends trust, policy, and verification.

## Understand and Apply Risk Management Concepts  
**Core idea:**  Risk management is the continuous process of identifying, analyzing, treating, and monitoring threats to organizational objectives.  

### Risk Terminology and Concepts  
- **Asset, threat, vulnerability, exposure, likelihood, impact, risk, residual risk.**  
- Risk = *threat × vulnerability × impact* (qualitative or quantitative).

### Asset Valuation  
- Assign **business value** (replacement cost, revenue stream, legal penalty).  
- Basis for cost/benefit and prioritization.

### Identify Threats and Vulnerabilities  
- Sources: natural, human, environmental, technological.  
- Use vulnerability scans, config reviews, threat intel.

### Risk Assessment/Analysis  
- **Quantitative** (SLE, ARO, ALE) vs **Qualitative** (heat maps, Delphi).  
- Output drives control selection and budgeting.

### Risk Responses  
- **Mitigate, transfer, avoid, accept, share**; document rationale.

### Cybersecurity Insurance  
- Transfers residual financial risk; review exclusions, coverage limits, and incident-notification clauses.

### Cost vs. Benefit of Security Controls  
- Implement when **annualized cost of control ≤ risk reduction (ALE savings)**.

### Countermeasure Selection and Implementation  
- Choose controls meeting **CIA** goals, regulatory needs, and feasibility.  
- Map to control catalogs (ISO 27002, NIST 800-53).

### Applicable Types of Controls  
- **Preventive, detective, corrective, deterrent, compensating, recovery, directive.**

### Security Control Assessment  
- Verify design & operational effectiveness (testing, audit, POA&M).

### Monitoring and Measurement  
- KPIs/KRIs, continuous monitoring dashboards, vulnerability metrics.

### Risk Reporting and Documentation  
- Audience-tailored reports to executives, regulators; maintain a risk register.

### Continuous Improvement  
- Follow **PDCA / NIST RMF Step 6**; feed incidents & metrics back into risk cycle.

### Legal Risk  
- Non-compliance fines, civil liability, criminal penalties; involve counsel in risk decisions.

### Risk Frameworks  
- **NIST RMF, ISO 31000, COSO ERM, FAIR, OCTAVE**—provide structure, roles, artifacts.

---

## Social Engineering  
**Core idea:**  Attackers exploit human trust to bypass technical controls; awareness training is the primary defense.  

### Social Engineering Principles  
- Authority, scarcity, urgency, liking, reciprocity, social proof, intimidation.

### Eliciting Information  
- Casual conversation, surveys, pretext calls to draw out sensitive details.

### Prepending  
- Injecting false context (e.g., “Re: Your invoice”) to gain trust.

### Phishing / Spear Phishing / Whaling  
- Mass, targeted, executive-targeted email attacks; defend with filtering + user training + MFA.

### Spam  
- Unsolicited messages; can carry malware, scams; use blacklists/DMARC.

### Shoulder Surfing  
- Visual hacking in public; mitigate with privacy screens, clean desk.

### Invoice Scams  
- BEC fraud; validate payment changes via out-of-band confirmation.

### Hoax  
- False alerts (e.g., fake virus warnings) cause self-inflicted disruption.

### Impersonation and Masquerading  
- Fake uniforms, badges, caller ID spoofing; enforce visitor procedures.

### Tailgating and Piggybacking  
- Following authorized user through door; use mantraps, employee vigilance.

### Dumpster Diving  
- Retrieving discarded sensitive info; mandate shredders and purge bins.

### Identity Fraud  
- Using stolen PII for credit or access; controls: KYC, MFA, fraud monitoring.

### Typosquatting  
- Register look-alike domains; implement defensive domain registration and browser URL filtering.

### Influence Campaigns  
- Disinformation to sway opinions; monitor social media, provide official comms.

---

## Establish and Maintain a Security Awareness, Education, and Training Program  
**Core idea:**  A tiered program (awareness → training → education) builds a culture of security and fulfills compliance mandates.  

### Awareness  
- Broad, brief messaging (posters, phishing banners) to keep security “top of mind.”

### Training  
- Role-based, task-focused (e.g., secure coding, data-handling).

### Education  
- Formal instruction (certifications, degrees) for career growth and deep expertise.

### Improvements  
- Update content for new threats, technologies, and lessons learned from incidents.

### Effectiveness Evaluation  
- Metrics: phishing click rate, quiz scores, incident reduction; adjust program based on data.

---

## Summary  
Personnel security weaves **HR processes**, **risk management**, and **human-factor defenses** into the overarching security program. Master the lifecycle from **screening → onboarding → oversight → offboarding**, apply formal **risk frameworks** to quantify and treat threats, and recognize social-engineering tactics so you can craft effective awareness, training, and contractual safeguards— all high-frequency CISSP exam fodder.

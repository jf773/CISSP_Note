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

#### Comparison Table: NDA Types
| NDA Type     | Description                                     | Use Case                          |
|--------------|--------------------------------------------------|-----------------------------------|
| Unilateral   | One-way: only one party discloses information   | Employer to employee              |
| Bilateral    | Both parties share and protect information      | Two companies in partnership      |
| Multilateral | Three or more parties share mutual information  | Consortiums or multi-party deals  |

> 🧠 Treat people as security partners, not just liabilities. A strong personnel security program blends trust, policy, and verification.

## Understand and Apply Risk Management Concepts  
**Core idea:**  Risk management is the continuous process of identifying, analyzing, treating, and monitoring threats to organizational objectives.  

### Risk Terminology and Concepts

Risk management is the process of identifying, evaluating, and mitigating risks to reduce them to an acceptable level.

#### Key Terms

| Term | Definition |
|------|------------|
| **Asset** | Anything of value used in a business process. |
| **Asset Valuation** | Assigning monetary/non-monetary value to assets. |
| **Threat** | Any potential danger that can exploit a vulnerability. |
| **Threat Agent / Actor** | The entity (person, group, software) that carries out the threat. |
| **Threat Event** | Actual occurrence of a threat (e.g., earthquake, fire, insider breach). |
| **Threat Vector** | The path used by a threat agent to exploit a vulnerability (e.g., phishing email, USB). |
| **Vulnerability** | A weakness in a system or lack of a safeguard. |
| **Exposure** | The condition of being exposed to a threat due to a vulnerability. |
| **Risk** | The probability of a threat exploiting a vulnerability and the resulting impact.<br>**Formula**: `Risk = Threat × Vulnerability` |
| **Safeguard / Countermeasure** | Controls used to mitigate vulnerabilities. |
| **Attack** | Deliberate act to exploit vulnerabilities. |
| **Breach** | A successful attack that bypasses security controls. |
| **Hazard** | A potential source of harm or adverse effect. |

🧠 **Memory Aid**: "Threats exploit vulnerabilities, causing risks that are reduced by safeguards."

### Asset Valuation

Asset valuation helps determine how much protection is warranted.

#### Factors in Valuation

- Purchase, development, and operational costs
- Intellectual property and replacement cost
- Value to the business, competitors, and market
- Liability if lost or compromised

📌 **Purpose of Asset Valuation**:
- Justify security expenditures
- Prioritize protection efforts
- Support cost-benefit analysis
- Establish insurance coverage

### Identify Threats and Vulnerabilities

Identify all threats to the environment:
- Natural (floods, fire)
- Technical (malware, system failure)
- Human (insider threats, social engineering)

📚 Refer to **NIST SP 800-30 Rev.1** Appendix D & E for categorized threats and events.

#### Team-Based Approach

- Involve cross-departmental members
- Consider external consultants and tools

### Risk Assessment/Analysis

Risk assessment evaluates threats to determine necessary controls.

#### Scope
Defines which assets, business units, or systems are covered.

#### Approaches

| Approach | Description |
|---------|-------------|
| **Asset-Based** | Starts with inventorying and valuing assets. |
| **Threat-Based** | Starts with threat identification and maps to vulnerable assets. |

#### Methodologies

| Type | Description |
|------|-------------|
| **Quantitative** | Uses formulas and financial data to calculate risk values. |
| **Qualitative** | Uses scenarios and expert opinion to categorize risk levels. |
| **Hybrid** | Combines both for a balanced approach. |

### Quantitative Risk Analysis

#### Key Formulas

```text
SLE = AV × EF
ALE = SLE × ARO
```

| Term | Definition |
|------|------------|
| **AV (Asset Value)** | Monetary worth of an asset. |
| **EF (Exposure Factor)** | Percentage of asset loss from an incident (0–1). |
| **SLE (Single Loss Expectancy)** | Monetary loss from one incident. |
| **ARO (Annualized Rate of Occurrence)** | Estimated yearly frequency of a threat. |
| **ALE (Annualized Loss Expectancy)** | Yearly potential loss from a threat. |

🧮 **Example**:  
If AV = $100,000, EF = 0.4 (40%), ARO = 1  
SLE = 100,000 × 0.4 = $40,000  
ALE = $40,000 × 1 = $40,000

#### Pros and Cons

| Feature | Qualitative | Quantitative |
|--------|-------------|--------------|
| Uses math | ❌ | ✅ |
| Fast & simple | ✅ | ❌ |
| Supports cost/benefit analysis | Limited | ✅ |
| Subjective | ✅ | ❌ |
| Automation support | ❌ | ✅ |

### Qualitative Risk Analysis

Uses expert judgment, surveys, and scenarios.

#### Tools
- Scenarios
- Delphi Technique (anonymous group consensus)
- Interviews and checklists

🧠 Use a 3x3 or 5x5 matrix to plot **Likelihood vs. Impact**.

### Risk Responses

| Response | Description |
|----------|-------------|
| **Mitigation** | Reduce risk by applying safeguards. |
| **Assignment (Transference)** | Shift risk via insurance or outsourcing. |
| **Avoidance** | Eliminate risk by stopping risky activities. |
| **Deterrence** | Discourage actions using warnings or penalties. |
| **Acceptance** | Acknowledge and accept risk (documented by management). |
| **Rejection** | Ignore the risk (⚠️ **not recommended**, may be seen as negligence). |

### Other Risk Concepts

| Concept | Description |
|--------|-------------|
| **Residual Risk** | Remaining risk after safeguards. |
| **Inherent Risk** | Risk before controls are applied. |
| **Total Risk** | AV × Threat × Vulnerability (no controls applied). |
| **Controls Gap** | Total Risk – Residual Risk. |
| **Control Risk** | New risk introduced by implementing a control. |
| **Risk Appetite** | Total risk an organization is willing to accept. |
| **Risk Tolerance** | Risk allowed per asset-threat pair. |
| **Risk Capacity** | Risk an organization is capable of handling.

✅ **Summary**

- Effective risk management requires a cycle of **assessment ➡ prioritization ➡ response ➡ re-assessment**.
- Use both qualitative and quantitative techniques to identify the highest priority risks.
- Always document and justify risk decisions, especially when accepting or transferring risk.

### Cybersecurity Insurance

Cybersecurity insurance (also known as cyber insurance or cyber risk insurance) is a type of insurance policy that provides coverage and financial protection against cyber-related incidents such as data breaches, cyberattacks, and system compromises. This is a form of **risk assignment response**.

#### Key Features
- **Data breach coverage**: Notification costs, credit monitoring, investigation, and mitigation.
- **Financial loss protection**: Includes theft, fraud, and extortion payments.
- **Legal liabilities**: Covers lawsuits, fines, and noncompliance penalties.
- **Reputation management**: PR and trust rebuilding expenses.
- **Business interruption**: Compensation for income loss due to downtime.
- **Ransomware protection**: Ransom payments, investigation, and remediation.
- **Forensic services**: Access to cybersecurity experts.
- **Incident response support**: Assistance during cyber events.
- **Regulatory compliance**: Coverage for fines and audits.
- **Third-party liability**: For damages caused to vendors/customers.

Organizations must evaluate **coverage limits, exclusions**, and **terms** carefully.

### Cost vs. Benefit of Security Controls

Security control decisions should be **cost-effective**, especially after a **quantitative risk assessment**. The basic principle is:

> **The cost of the safeguard should not exceed the benefit of the risk reduction.**

#### Formula for Cost/Benefit
```
(ALE1 – ALE2) – ACS = Value of the Safeguard
```

- **ALE1**: Annualized Loss Expectancy before safeguard
- **ALE2**: ALE after safeguard
- **ACS**: Annual Cost of the Safeguard

If the result is positive, the safeguard is economically justifiable.

#### Annual Cost of Safeguard (ACS) includes:
- Development & licensing
- Implementation/customization
- Maintenance
- Training/productivity impacts
- Testing and auditing costs

#### Table: Risk Assessment Formulas
| Concept                         | Formula/Meaning                     |
|-------------------------------|------------------------------------|
| Asset Value (AV)              | $                                  |
| Exposure Factor (EF)          | % Loss                             |
| Single Loss Expectancy (SLE)  | SLE = AV × EF                      |
| Annualized Rate of Occurrence (ARO) | # per year                   |
| Annualized Loss Expectancy (ALE) | ALE = SLE × ARO or AV × EF × ARO |
| Cost/Benefit of Safeguard     | (ALE1 – ALE2) – ACS                |

Also consider **legal, regulatory, and due care** responsibilities when evaluating control cost.

### Countermeasure Selection and Implementation

Choosing effective safeguards requires considering:

- 🔒 **Cost < Value of Asset**
- 🔒 **Cost < Benefit**
- 🔒 **Makes attacks costlier than their rewards**
- 🔒 **Addresses real problems, not just trends**
- 🔒 **Remains effective even if known**
- 🔒 **Consistent across systems/users**
- 🔒 **Testable/verifiable**
- 🔒 **Fails safe or secure**

Security should **enable** business functions, not obstruct them.

#### Control Categories in Defense-in-Depth
1. **Administrative (Managerial)**: Policies, training, background checks, classification.
2. **Technical (Logical)**: Authentication, encryption, firewalls, IDS/IPS.
3. **Physical**: Locks, cameras, guards, fences, motion detectors.

### Applicable Types of Controls

| Type          | Purpose                                               | Examples                                           |
|---------------|--------------------------------------------------------|----------------------------------------------------|
| Preventive    | Prevent incident                                       | Locks, firewalls, access control, encryption       |
| Detective     | Detect occurrence                                     | IDS, logs, surveillance, audits                    |
| Corrective    | Fix system, mitigate after incident                   | IPS, reboots, file restoration                     |
| Recovery      | Restore capabilities post-incident                    | Backups, clustering, alternate sites              |
| Deterrent     | Discourage attackers                                  | Signage, cameras, training                         |
| Directive     | Mandate behavior                                      | Policies, procedures, supervision                  |
| Compensating  | Substitute or support other controls                  | Backup for failed prevention, alternate workflows |

No single control is perfect—use **defense in depth**.

### Security Control Assessment (SCA)

A **Security Control Assessment** (SCA) is the formal evaluation of security controls against defined baselines (e.g., NIST SP 800-53 Rev. 5).

#### Goals
- Validate control **effectiveness**
- Assess **risk management** practices
- Identify **strengths/weaknesses** in implementation
- Evaluate **privacy impact** of security controls

#### Key Points
- May be part of broader penetration testing or vulnerability assessments.
- Should assess **operational**, **technical**, and **privacy-related** risks.
- Adopted by **federal agencies**, but valuable for all organizations.

### Monitoring and Measurement

Security controls must be **continuously monitored and measured** to validate their effectiveness. Controls that cannot be quantified or evaluated offer questionable value.

#### Key Concepts:
- Some controls have **native monitoring**, others require **external validation**.
- Metrics require a known **baseline** (pre-control state).
- Not all improvements can be quantified in hard numbers.
- Measurement helps in **cost/benefit justification**.

> Significant improvement must be demonstrated to justify the deployment cost.

### Risk Reporting and Documentation

**Risk reporting** ensures stakeholders receive necessary updates about risk posture.

#### Internal Reporting
- Targets executives, managers, and employees.
- Contains: risk registers, key risk indicators (KRIs), heat maps, mitigation effectiveness.

#### External Reporting
- For regulators, shareholders, and public transparency.
- Includes: disclosures, annual reports, regulatory filings.

#### Risk Register Contents
- Identified risks
- Risk severity and prioritization
- Mitigation strategies
- Tracking progress

#### Risk Matrix (Heat Map)
- Visual risk assessment using a grid (e.g., 3×3 for likelihood × impact).
- Helps prioritize risks based on severity.

### Continuous Improvement

Security is **not static**—risk assessments must evolve.

#### Key Points
- Risk assessment is a **point-in-time metric**.
- **Continuous reassessment** is essential.
- Reassess threats, vulnerabilities, and business context regularly.
- Replace outdated countermeasures lacking scalability.

#### Risk Maturity Model (RMM) Levels
1. **Ad hoc**: Chaos, no consistency.
2. **Preliminary**: Departmental variation in process.
3. **Defined**: Standardized org-wide process.
4. **Integrated**: Metrics used, risk embedded in strategy.
5. **Optimized**: Risk is managed strategically, lessons reintegrated.

### Legal Risk

Legacy systems represent a serious **security and compliance risk**.

#### Definitions
- **EOL (End of Life)**: Product no longer produced.
- **EOSL (End of Service Life)**: No support, patches, or updates.

> EOSL systems must be replaced to avoid unpatchable vulnerabilities.

#### Example
- Windows 10 reaches EOSL on **October 14, 2025**.
- Vendors recommend transitioning to supported versions (e.g., Windows 11).

### Risk Frameworks

A **risk framework** guides how risk is identified, assessed, and mitigated.

#### NIST Cybersecurity Framework (CSF 2.0)
Six core functions:
1. **Identify**: Assets, risks, vulnerabilities
2. **Protect**: Implement safeguards
3. **Detect**: Monitoring and alerting
4. **Respond**: Incident response
5. **Recover**: Business continuity
6. **Govern**: Oversight, roles, policies

> CSF is prescriptive and improvement-focused—not a checklist.

#### NIST Risk Management Framework (RMF - SP 800-37 Rev. 2)
Seven RMF phases:
1. **Prepare**: Define context and priorities
2. **Categorize**: Analyze system impact
3. **Select**: Tailor controls
4. **Implement**: Deploy controls
5. **Assess**: Validate effectiveness
6. **Authorize**: Approve system for operation
7. **Monitor**: Ongoing evaluation

#### ISO Risk Standards
- **ISO/IEC 31000**: General guidelines for any organization
- **ISO/IEC 27005**: Specific to information security risk
- **ISO/IEC 31004**: Guidance on implementing ISO 31000 (now withdrawn)

#### Other Frameworks for Reference
- **COSO ERM**
- **ISACA Risk IT Framework**
- **OCTAVE**
- **FAIR (Factor Analysis of Information Risk)**
- **TARA (Threat Assessment and Remediation Analysis)**

> Framework selection depends on your organization's size, industry, and risk profile.

## Social Engineering

Social engineering exploits human behavior to gain unauthorized access or information. Attackers manipulate trust, urgency, authority, and other psychological triggers to deceive victims into compromising security.

### Social Engineering Principles

1. **Authority**: Attackers pose as figures of authority (e.g., CEO) to gain compliance.
2. **Intimidation**: Uses fear, threats, or pressure to influence actions.
3. **Consensus/Social Proof**: Convince targets by claiming others have taken similar actions.
4. **Scarcity**: Suggest limited-time opportunities to invoke urgency.
5. **Familiarity/Liking**: Leverages shared interests, backgrounds, or mutual acquaintances.
6. **Trust**: Builds a false relationship to manipulate behavior.
7. **Urgency**: Pressures targets to act before they can think critically.

### Eliciting Information

Eliciting is gathering intelligence through casual conversation or questioning to build more effective attacks. Often used in reconnaissance phases.

**Defenses**:
- Classify sensitive data
- Train personnel
- Monitor and report suspicious activity

### Prepending

Prepending adds misleading headers or prefixes to deceive users or bypass filters.

**Examples**:
- Using "RE:" or "FW:" in phishing subjects
- Spoofing headers like "X-Spam-Category: LEGIT"

### Phishing

Mass-targeted attacks to steal credentials or install malware via deceptive emails.

**Defenses**:
- User awareness training
- Never click unknown links or attachments
- Use bookmarks instead of email links
- Deploy email filters and DMARC, SPF, DKIM

### Spear Phishing

Targeted phishing aimed at specific individuals or organizations, often using personal data.

**Example**: Business Email Compromise (BEC) where attackers pose as executives.

**Defenses**:
- Label sensitive info
- Validate unusual requests out-of-band
- Block atypical purchasing behavior

### Whaling

A type of spear phishing aimed at high-value individuals like CEOs.

**Traits**:
- Highly personalized
- Often sophisticated and well-researched

### Spam

Unwanted or unsolicited messages, often carrying malicious payloads or links.

**Defenses**:
- Spam filters
- Client and server-side filtering
- Use of DMARC, SPF, DKIM to block spoofing

### Shoulder Surfing

Physical observation of user screens or input.

**Defenses**:
- Use screen filters
- Position monitors away from view
- Mask password entry fields
- Control physical access

### Invoice Scams

Invoice scams are social engineering attacks involving fake invoices sent to organizations or individuals with the goal of tricking them into transferring funds to the attacker.

#### Characteristics
- Often targets accounting or finance departments.
- May impersonate executives (e.g., Business Email Compromise).
- Can be executed via email or phone (voice phishing).

#### Defenses
- Enforce **purchase order (PO) matching**.
- Implement **separation of duties** between ordering and payment teams.
- **Verify** all invoices via **face-to-face or out-of-band communication**.
- **Audit** invoice and billing activities regularly.
- **Report** all fraudulent invoices to law enforcement.

### Hoax

A hoax is a deceptive message urging recipients to take harmful actions under false pretenses.

#### Examples
- Fake virus alerts prompting users to delete system files.
- Instructions to install fake security software.
- Requests to forward warning messages to others.

#### Defenses
- **Educate users** to be skeptical of unsolicited warnings.
- Use **trusted verification sources** like snopes.com or phishtank.com.
- Never **forward unverified messages**.

### Impersonation and Masquerading

Impersonation involves pretending to be someone else to gain access or information.

#### Variants
- **Masquerading**: Less sophisticated imitation (e.g., costume).
- **Spoofing**: Faking caller ID, email, or identity credentials.
- **Identity Fraud**: Using stolen identity for financial or personal gain.

#### Defenses
- Require **ID verification** at physical entrances.
- Enforce **visitor escort policies**.
- **Pre-approve** visits with security team.

### Tailgating and Piggybacking

Physical entry attacks exploiting social behavior.

#### Tailgating
- **No consent**: Attacker slips in behind authorized user.

#### Piggybacking
- **With consent**: Victim is tricked into holding door open.

#### Defenses
- Train users to **close doors immediately**.
- Use **mantraps**, **turnstiles**, and **access logs**.
- **Request credentials** before granting access.

### Dumpster Diving

Attackers search trash or recycling for useful information.

#### Common Finds
- Printed documents
- Sticky notes
- Product packaging
- Discarded media or hardware

#### Defenses
- **Shred** or **incinerate** documents.
- Use **certified media destruction services**.

### Identity Fraud

Misuse of personal data to impersonate or steal financial resources.

#### Identity Theft vs. Identity Fraud
- **Theft**: Stealing information (SSN, passwords, etc.).
- **Fraud**: Using that information to impersonate someone.

#### Defenses
- Educate employees on **PII protection**.
- Monitor for **anomalous account activity**.
- Use **strong authentication**.

### Typosquatting

Malicious registration of mistyped domain names to mislead users.

#### Techniques
- Misspellings (e.g., `googel.com`)
- Extra characters (`gooogle.com`)
- Alternate TLDs (`google.net`, `google.co`)

#### Defenses
- Educate users to **double-check URLs**.
- Register **common variations** of your domain.
- Monitor for **fake domains** impersonating your brand.

### Influence Campaigns

Coordinated efforts to manipulate public opinion using false or misleading content.

#### Key Concepts
- **Disinformation**: Deliberate lies.
- **Misinformation**: Mistakes shared as truth.
- **Propaganda**: Biased material to shape opinion.
- **Doxing**: Publishing private data to intimidate or harass.

#### Delivery Vectors
- Social media
- Fake news websites
- Hacked forums
- Hybrid warfare (cyber + psychological + political)

#### Defenses
- Promote **media literacy** and **critical thinking**.
- **Block social media** where necessary at work.
- Monitor for **emerging disinformation narratives**.

## Establish and Maintain a Security Awareness, Education, and Training Program

The effectiveness of a security solution relies not only on technology but on people changing their behavior to align with organizational security goals.

### Awareness

- **Definition**: Awareness aims to establish a baseline understanding of security across all users.
- **Goal**: Bring attention to security issues, responsibilities, and best practices.
- **Methods**:
  - Posters, newsletters, email tips
  - Screensavers with reminders
  - Instructor-led sessions
- **Important Note**: Awareness applies to everyone — including executives.

### Training

- **Definition**: Training is task-specific instruction that ensures employees perform securely.
- **Scope**:
  - Role-based
  - Ongoing
  - New employee onboarding
- **Control Type**: Administrative control
- **Evaluation Methods**:
  - Post-training quizzes
  - Performance tracking
  - Incident reduction analysis

### Education

- **Definition**: Broader and more in-depth than training; focuses on comprehensive understanding.
- **Target Audience**:
  - Security professionals
  - Candidates for promotions or certifications
- **Includes**:
  - Micro-learning (mobile-based, bite-sized content)
  - External training providers

### Improvements

- **Techniques**:
  - Rotate topics and target audiences
  - Vary formats: in-person, videos, VR, simulations
  - Role-playing and security champions
- **Gamification Elements**:
  - Points, badges, challenges
  - Capture-the-flag, phishing simulations
  - Rewards for secure behavior

### Effectiveness Evaluation

- **Purpose**: Measure if training leads to behavior change and reduced incidents.
- **Evaluation Methods**:
  - Immediate and delayed quizzes
  - Log analysis for incident trends
  - Content reviews for relevance
- **Emerging Topics**:
  - AI, blockchain, cryptocurrency
- **Violation Analysis**:
  - Determine if incident was accidental or malicious
  - Train or discipline accordingly

## Summary

- **Security Planning**:
  - Job descriptions, background checks, NDA
  - Onboarding, offboarding, access reviews
- **Risk Management**:
  - Identify, analyze, respond to risks
  - Acceptable risk levels vary by organization
- **Social Engineering**:
  - Attackers exploit human behavior
  - Defenses include user education and awareness
- **Common Techniques**:
  - Phishing, whaling, tailgating, dumpster diving
- **Learning Levels**:
  - Awareness (basic), Training (job tasks), Education (professional depth)
- **Program Enhancements**:
  - Security champions
  - Gamification
  - Continuous evaluation

> Behavior change through education is the foundation of strong security culture.

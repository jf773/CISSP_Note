# Chapter 8: Principles of Security Models, Design, and Capabilities

- [Secure Design Principles](#secure-design-principles)
  - [Objects and Subjects](#objects-and-subjects)
  - [Closed and Open Systems](#closed-and-open-systems)
    - [APIs and Interoperability](#apis-and-interoperability)
    - [Open Source vs Closed Source](#open-source-vs-closed-source)
  - [Secure Defaults](#secure-defaults)
    - [Restrictive Defaults](#restrictive-defaults)
  - [Fail Securely](#fail-securely)
    - [Fail-Open vs Fail-Closed](#fail-open-vs-fail-closed)
    - [Fail-Safe vs Fail-Secure](#fail-safe-vs-fail-secure)
    - [Stop Error and BSoD](#stop-error-and-bsod)
  - [Keep It Simple and Small (KISS)](#keep-it-simple-and-small-kiss)
    - [DRY, YAGNI, Minimalism](#dry-yagni-minimalism)
  - [Zero Trust](#zero-trust)
    - [Microsegmentation](#microsegmentation)
    - [Real-time Monitoring](#real-time-monitoring)
    - [Air Gap and Faraday Cage](#air-gap-and-faraday-cage)
  - [Trust but Verify](#trust-but-verify)
  - [Privacy by Design (PbD)](#privacy-by-design-pbd)
    - [7 Foundational Principles](#7-foundational-principles)
    - [Global Privacy Standard (GPS)](#global-privacy-standard-gps)
  - [Secure Access Service Edge (SASE)](#secure-access-service-edge-sase)
    - [Cloud-Native and Identity-Centric](#cloud-native-and-identity-centric)
    - [ZTNA, Edge Computing, Monitoring](#ztna-edge-computing-monitoring)
- [Techniques for Ensuring CIA](#techniques-for-ensuring-cia)
  - [Confinement](#confinement)
  - [Bounds](#bounds)
  - [Isolation](#isolation)
  - [Access Controls](#access-controls)
  - [Trust and Assurance](#trust-and-assurance)
- [Understand the Fundamental Concepts of Security Models](#understand-the-fundamental-concepts-of-security-models)
  - [Tokens, Capabilities, and Labels](#tokens-capabilities-and-labels)
  - [Trusted Computing Base (TCB)](#trusted-computing-base-tcb)
    - [Security Perimeter](#security-perimeter)
    - [Reference Monitor and Security Kernel](#reference-monitor-and-security-kernel)
  - [State Machine Model](#state-machine-model)
  - [Information Flow Model](#information-flow-model)
  - [Noninterference Model](#noninterference-model)
  - [Composition Theories](#composition-theories)
    - [Cascading](#cascading)
    - [Feedback](#feedback)
    - [Hookup](#hookup)
  - [Take-Grant Model](#take-grant-model)
  - [Access Control Matrix](#access-control-matrix)
  - [Bell–LaPadula Model](#bell-lapadula-model)
    - [Lattice-Based Access Control](#lattice-based-access-control)
    - [Simple Security Property](#simple-security-property)
    - [Star (*) Property](#star-property)
    - [Discretionary Security Property](#discretionary-security-property)
  - [Biba Model](#biba-model)
    - [Simple Integrity Property](#simple-integrity-property)
    - [Star (*) Integrity Property](#star-integrity-property)
    - [Invocation Property](#invocation-property)
  - [Clark–Wilson Model](#clark-wilson-model)
    - [Constrained and Unconstrained Data Items](#constrained-and-unconstrained-data-items)
    - [Integrity Verification Procedures (IVPs)](#integrity-verification-procedures-ivps)
    - [Transformation Procedures (TPs)](#transformation-procedures-tps)
  - [Brewer and Nash Model](#brewer-and-nash-model)
    - [Conflict of Interest and Dynamic Domains](#conflict-of-interest-and-dynamic-domains)
    - [Deprecated: Chinese Wall Model](#deprecated-chinese-wall-model)
  - [Disambiguating the Word “Star” in Models](#disambiguating-the-word-star-in-models)
- [Select Controls Based on Systems Security Requirements](#select-controls-based-on-systems-security-requirements)
  - [Common Criteria](#common-criteria)
    - [Protection Profiles (PPs)](#protection-profiles-pps)
    - [Security Targets (STs)](#security-targets-sts)
    - [Evaluation Assurance Levels (EALs)](#evaluation-assurance-levels-eals)
  - [Authorization to Operate (ATO)](#authorization-to-operate-ato)
    - [Authorizing Official (AO)](#authorizing-official-ao)
    - [Types of Authorization Decisions](#types-of-authorization-decisions)
- [Understand Security Capabilities of Information Systems](#understand-security-capabilities-of-information-systems)
  - [Memory Protection](#memory-protection)
  - [Virtualization](#virtualization)
  - [Trusted Platform Module (TPM)](#trusted-platform-module-tpm)
  - [Interfaces](#interfaces)
  - [Fault Tolerance](#fault-tolerance)
  - [Encryption/Decryption](#encryptiondecryption)
  - [Manage the Information System Life Cycle](#manage-the-information-system-life-cycle)
    - [Stakeholders' Needs and Requirements](#stakeholders-needs-and-requirements)
    - [Requirements Analysis](#requirements-analysis)
    - [Architectural Design](#architectural-design)
    - [Development/Implementation](#developmentimplementation)
    - [Integration](#integration)
    - [Verification and Validation](#verification-and-validation)
    - [Transition/Deployment](#transitiondeployment)
    - [Operations and Maintenance/Sustainment](#operations-and-maintenancesustainment)
    - [Retirement/Disposal](#retirementdisposal)
- [Summary](#summary)

## Secure Design Principles

### Objects and Subjects

In information security, all access control is based on the **interaction between subjects and objects**.

- A **subject** is an active entity (e.g., user, process, program) that requests access to a resource.
- An **object** is a passive entity (e.g., file, printer, database) that contains or receives data and is acted upon.

This model helps define **who can do what to which resources**, forming the foundation for **access control mechanisms** like DAC, MAC, and RBAC.

#### Subject-Object Relationship
The **access control system** determines how subjects can interact with objects. Examples include:
- User (subject) reading a document (object)
- Process writing to a log file
- Program executing another process

| Term    | Description                                  |
|---------|----------------------------------------------|
| Subject | Active entity requesting access               |
| Object  | Passive entity being accessed                 |
| Access  | The operation (read/write/execute) performed  |

🧠 **CISSP Insight**: Every access control mechanism uses subjects and objects to define permissions, restrictions, and enforcement boundaries.

#### Dynamic Roles
An entity can act as a subject in one context and as an object in another.
- Example:
  - Process A (subject) → Process B (object)
  - Process B (now subject) → Process C (object)

This flexible interpretation is important in **multi-threaded systems**, **inter-process communication**, and **chained execution flows**.

#### Transitive Trust

**Transitive trust** occurs when a subject inherits or extends trust through an intermediary entity.

- If A trusts B, and B trusts C, then A may **implicitly trust** C.
- This chain can lead to **unintended access** and **security gaps** if not carefully managed.

🚨 **Exam Warning**: Transitive trust is especially dangerous in federated systems and cloud-based environments. Always evaluate the **full trust chain**.

#### Access Rules
Access control models implement rules to govern subject-object interactions:
- **Discretionary Access Control (DAC)**: Subject owns the object and defines access.
- **Mandatory Access Control (MAC)**: Access is based on labels (e.g., Top Secret).
- **Role-Based Access Control (RBAC)**: Access based on user roles.

🛡️ **CISSP Exam Tip**: Know which models use subjects/objects explicitly and how **subject-object pairs** are evaluated for permissions.

#### Summary

- The subject-object model defines **who interacts with what**, and **how**.
- It is fundamental to **access control**, **system design**, and **security model implementation**.
- Understanding this relationship helps identify **risk points** and enforce **least privilege**.

| Concept           | Summary                                                                 |
|------------------|-------------------------------------------------------------------------|
| Subject           | Active initiator of access (user/process)                              |
| Object            | Passive target of access (file/device)                                 |
| Access Control    | Restricts which subjects can perform which actions on which objects     |
| Transitive Trust  | Indirect trust that can extend across systems; may be unsafe            |
| Dynamic Behavior  | Same entity can act as subject or object depending on context           |

### Closed and Open Systems

Closed and open systems describe **how much visibility and control** an organization or developer has over the internal mechanisms of a system. These classifications influence **interoperability, security review, and trust**.

#### Closed Systems
A **closed system** is proprietary and restricted:
- The **internal workings are not shared** publicly.
- Typically developed by a **single organization or vendor**.
- Requires **vendor support** for updates, patches, and integrations.
- Can create **vendor lock-in** and **limited transparency**.

Advantages:
- Centralized control
- Consistency and product support

Disadvantages:
- Difficult to audit for vulnerabilities
- Limited interoperability with third-party systems

🔒 **Example**: Microsoft Windows source code is closed—only Microsoft can modify it.

#### Open Systems
An **open system** is designed with **public interfaces, standards, and transparency**:
- Encourages **interoperability** and **community collaboration**.
- Source code or system documentation is often **accessible** or **open**.
- Supports **open standards** for easier integration.

Advantages:
- Easier to audit and test
- Often community-driven improvements
- Less vendor dependency

Disadvantages:
- Greater variation in implementation quality
- May require more effort to maintain or support

🌍 **Example**: Linux distributions like Ubuntu are considered open systems.

#### APIs and Interoperability

**APIs (Application Programming Interfaces)** enable **interoperability** between open and closed systems by defining how software components interact.

- Well-documented APIs can allow **secure, controlled access** to core functionality.
- Open systems often expose APIs for external developers.
- Closed systems may offer **limited or proprietary APIs** only under strict licensing.

🧩 **Interoperability** is key for:
- Enabling multi-vendor environments
- Reducing vendor lock-in
- Supporting hybrid architectures (e.g., cloud + on-prem)

#### Open Source vs Closed Source

| Category       | Open Source                              | Closed Source                               |
|----------------|-------------------------------------------|----------------------------------------------|
| Access         | Publicly viewable and modifiable code     | Proprietary code controlled by vendor        |
| Transparency   | High (anyone can inspect code)            | Low (security by obscurity risk)             |
| Community      | Often developed collaboratively           | Developed internally                         |
| Customization  | Highly customizable                       | Limited customization                        |
| Support        | Community and vendor options (varied)     | Official vendor support                      |
| Licensing      | GPL, MIT, Apache, etc.                    | Vendor-specific EULA                         |

💡 **CISSP Insight**: Open source is not inherently secure. It allows inspection, but security depends on **code quality**, **patching discipline**, and **community support**.

#### Summary

Closed and open systems differ in **transparency**, **control**, and **integration**:
- Closed systems offer consistency and control but may restrict visibility.
- Open systems enable interoperability and inspection but require more due diligence.
- APIs bridge both models and facilitate secure system integration.
- Exam questions may test your ability to evaluate **risk**, **trust**, and **integration complexity** based on system type.

🛡️ **CISSP Exam Tip**: Don’t confuse open source with secure by default. Know when each model is appropriate based on business needs and threat posture.

### Secure Defaults

**Secure defaults** refer to configuring systems and applications in their **most secure state by default**, minimizing the attack surface **before any customization or deployment**.

Many breaches occur because default settings are **insecure**, left unchanged, or overly permissive.

#### Why Secure Defaults Matter

When systems ship with:
- Open ports
- Default credentials
- Unrestricted access
…they become **low-hanging fruit** for attackers.

Secure defaults embody the **principle of least privilege** — every user, process, and service should have the **minimum access necessary**.

🛡️ **CISSP Insight**: Secure defaults enforce protection *before* users or admins apply hardening. They're proactive defenses.

#### Key Principles of Secure Defaults

- **Disable unnecessary services**: Fewer services = fewer attack vectors.
- **Use restrictive access controls**: Deny by default, explicitly allow only trusted actions.
- **Disable guest accounts and default passwords**: Often exploited in attacks.
- **Enable logging and auditing by default**: Ensure traceability.
- **Secure installation paths**: Avoid executing from temporary or user-writable directories.
- **Minimal feature sets**: Only enable essential functionality.

#### Restrictive Defaults

A **restrictive default posture** means that **all access is denied unless explicitly granted**.

- Example: A firewall drops all traffic unless a rule permits it.
- Encourages **intentional, controlled configuration**.
- Follows the **"deny-by-default"** model.

| Configuration Style | Description                                        | Security Posture     |
|---------------------|----------------------------------------------------|-----------------------|
| Open by Default     | Services and access are broadly enabled            | ❌ High risk          |
| Restrictive Default | Nothing is accessible until explicitly permitted   | ✅ Secure and auditable |

🚨 **Exam Reminder**: Systems should not rely on users to manually secure configurations. The **default** should already be hardened.

#### Common Violations of Secure Defaults

- Leaving **SSH or RDP open** to the internet
- Using **admin/admin** or **root/toor** as default credentials
- Web servers with **directory listing enabled**
- Databases with **blank or default passwords**

✅ **Fix**: Apply configuration management and compliance scanning to enforce secure settings.

#### Summary

Secure defaults reduce risk by:
- Disabling risky features
- Enforcing least privilege
- Denying access by default
- Promoting intentional and secure configurations

| Concept               | Summary                                                                 |
|-----------------------|-------------------------------------------------------------------------|
| Secure Defaults        | Preconfigured to the most secure state possible                        |
| Restrictive Defaults   | Deny all by default, explicitly allow only necessary access             |
| Common Violations      | Unused services enabled, default passwords, open ports                  |
| Risk Reduction         | Secure defaults reduce reliance on users to harden systems post-deploy |

🔑 **CISSP Exam Tip**: Remember — **security should be opt-out, not opt-in**. Always favor **secure defaults** in system design.

### Fail Securely

**Fail securely** means that when a system, component, or control encounters an error or failure, it **defaults to a secure state**—not an open or permissive one.

This principle ensures that **security is preserved even during abnormal conditions** such as power failures, application crashes, or denied access attempts.

#### Key Concepts of Failing Securely

- If **authorization cannot be verified**, access should be denied.
- If a system **crashes or loses power**, sensitive data should not be exposed.
- If an error occurs during input validation, the input should be **rejected**, not accepted.

🛡️ **CISSP Exam Insight**: Systems should never fail in a way that bypasses security controls or exposes sensitive data.

#### Fail-Open vs Fail-Closed

| Fail Behavior | Description                                         | Security Implication |
|---------------|-----------------------------------------------------|-----------------------|
| **Fail-Open**  | Allows access or functionality when failure occurs  | ❌ High risk          |
| **Fail-Closed**| Denies access and halts operation on failure        | ✅ Secure option      |

**Fail-closed** is the preferred secure behavior.

**Example**:
- A firewall should **fail-closed**, blocking traffic if rules cannot be loaded.
- An access control mechanism should deny entry if authentication fails, not allow a bypass.

#### Fail-Safe vs Fail-Secure

These terms are sometimes used interchangeably, but have subtle differences:

| Term        | Context                | Behavior on Failure                             |
|-------------|------------------------|--------------------------------------------------|
| Fail-Safe   | **Safety-first**       | Prioritizes human safety over security (e.g., unlock doors during a fire) |
| Fail-Secure | **Security-first**     | Maintains security posture even if inconvenient (e.g., locked doors during a fire) |

⚠️ **CISSP Exam Note**: Know the difference. Fail-safe = physical safety; fail-secure = data/security protection.

#### Stop Error and BSoD

- A **stop error** (e.g., Windows **Blue Screen of Death (BSoD)**) halts the system when a critical fault occurs.
- While disruptive, it may be **intentional to prevent further damage** or corruption.

🧠 **Security Perspective**:
- Crashes are not inherently secure unless they **preserve confidentiality and integrity** during the failure.
- Systems must log the failure, retain audit trails, and **not expose data in memory**.

#### Summary

Failing securely ensures that when things go wrong, they do so **safely and securely**, preventing data leaks or unauthorized access.

| Concept              | Summary                                                                |
|----------------------|------------------------------------------------------------------------|
| Fail-Closed          | Deny access or halt system upon failure (secure default)               |
| Fail-Open            | Allow access upon failure (dangerous, avoid unless safety-critical)     |
| Fail-Safe            | Prioritize physical safety (e.g., exit doors unlock during emergencies) |
| Fail-Secure          | Prioritize system/data security (e.g., remain locked on power loss)     |
| BSoD/Stop Error      | Forceful system halt to prevent further errors—may help preserve integrity |

✅ **CISSP Exam Tip**: When designing controls, ask: “If this fails, does it fail in a way that protects or exposes the system?”

### Keep It Simple and Small (KISS)

The **Keep It Simple and Small (KISS)** principle emphasizes simplicity in design to enhance security, reliability, and maintainability. In the context of security architecture, **complex systems are harder to secure, audit, and understand**, increasing the risk of misconfiguration and undetected vulnerabilities.

🧠 **CISSP Insight**: Complexity is the enemy of security. Simpler designs are more likely to be **secure by default** and easier to evaluate or test.

#### Principle Overview

- Originates from military and engineering practices: “Simple systems fail less.”
- Encourages minimal features and straightforward logic.
- Smaller codebases and systems have **fewer attack surfaces**.
- Reduces the likelihood of errors, misconfigurations, and hidden backdoors.

#### Benefits of KISS in Security

| Benefit               | Description                                                                          |
|-----------------------|--------------------------------------------------------------------------------------|
| Fewer Attack Vectors  | Less complexity = fewer potential exploits                                          |
| Easier Auditing       | Simpler systems are easier to understand, test, and validate                        |
| Faster Patching       | Less code means bugs can be found and fixed more quickly                            |
| Better Maintainability| Less chance of introducing errors when making changes                               |
| Improved Availability | Fewer components mean less can go wrong                                             |

#### Related Design Principles

##### DRY (Don’t Repeat Yourself)
- Avoid duplication in code and logic.
- Changes only need to happen in one place—reduces errors and inconsistencies.

##### YAGNI (You Aren’t Gonna Need It)
- Only implement features that are absolutely necessary.
- Unused features can create **dead code**, increasing the attack surface.

##### Minimalism in Security
- The fewer modules, services, and ports exposed, the better.
- Use **minimal default installations**, turning off unnecessary functions.

🛡️ **Exam Tip**: You may encounter scenarios where a system with fewer functions is preferred because it adheres to KISS and minimizes risk.

#### Example in Practice

- Instead of a full-featured mail server with dozens of unnecessary services, deploy a lightweight MTA (Mail Transfer Agent) that only relays outbound email.
- Disable unused Windows features and services rather than leaving them running "just in case."

#### Summary

The **KISS principle** supports security through **simplification**. By reducing complexity, organizations can:
- Limit vulnerabilities
- Simplify audits
- Ensure systems behave predictably

| Concept       | Summary                                                          |
|---------------|------------------------------------------------------------------|
| KISS          | Design systems to be simple and minimal                          |
| DRY           | Avoid redundancy to simplify updates and reduce risk             |
| YAGNI         | Don’t build features you don’t currently need                    |
| Minimalism    | Fewer services and features = smaller attack surface             |

🔍 **CISSP Reminder**: KISS applies not only to application code but also to **system architecture, policies, and security configurations**.

### Zero Trust

**Zero Trust** is a modern security architecture and mindset based on the principle:  
> **“Never trust, always verify.”**

It assumes that **no user, device, or system—internal or external—should be automatically trusted**. Every access request must be continuously validated based on identity, context, and risk.

🛡️ **CISSP Exam Insight**: Zero Trust is not a single product—it’s a strategy involving **identity verification, access controls, segmentation, and monitoring**.

#### Core Principles of Zero Trust

1. **Verify explicitly**  
   - Always authenticate and authorize based on all available data (user identity, device health, location, etc.).

2. **Use least privilege access**  
   - Limit user and device access to only what is needed for their role (principle of least privilege).

3. **Assume breach**  
   - Design systems under the assumption that attackers are already inside the network.

#### Key Components of Zero Trust

| Component                | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| Identity & Access Management (IAM) | Strong authentication (MFA), continuous session validation         |
| Network Segmentation     | Divides networks into small segments to contain threats                    |
| Endpoint Security        | Ensures device compliance (e.g., up-to-date patches, EDR agents)           |
| Monitoring & Analytics   | Detect anomalies and potential breaches in real-time                       |

#### Microsegmentation

Microsegmentation breaks the network into **fine-grained zones**, applying access controls at the **workload or process level** rather than the perimeter.

- Limits lateral movement
- Isolates breaches
- Enforced with tools like **NGFW**, **SDN**, and **host-based firewalls**

🧱 Example:
A compromised printer on the guest VLAN cannot access sensitive finance servers.

#### Real-time Monitoring

Zero Trust emphasizes **continuous monitoring** for authentication, network behavior, and data access.

- Leverages tools like **UEBA (User and Entity Behavior Analytics)** and **SIEM**
- Detects and responds to threats **before damage occurs**
- Integrates with incident response workflows

📌 **CISSP Note**: Zero Trust doesn’t mean trusting nothing—it means **verifying everything**, all the time.

#### Air Gap and Faraday Cage

To support Zero Trust at the **physical level**, organizations may implement:

- **Air Gap**: Complete disconnection from other networks (often used in ICS/SCADA).
- **Faraday Cage**: Enclosure that blocks electromagnetic signals to prevent wireless data leaks or eavesdropping.

🔒 These methods enforce physical isolation and prevent **covert channels**.

#### Summary

Zero Trust is a **strategic model** that enforces **strong authentication, granular authorization, and continuous monitoring** to reduce risk across complex environments.

| Concept                | Summary                                                                 |
|------------------------|-------------------------------------------------------------------------|
| Zero Trust             | Never trust, always verify—even inside the perimeter                    |
| Microsegmentation      | Small, isolated zones prevent lateral movement                          |
| Real-time Monitoring   | Detect threats based on behavior, identity, and session context         |
| Air Gap / Faraday Cage | Enforce physical and electromagnetic isolation                          |
| Principle of Least Privilege | Critical to Zero Trust—access only what is absolutely necessary    |

🔐 **CISSP Tip**: Expect exam questions that test Zero Trust as a **comprehensive architecture**, not just a technical control.

### Trust but Verify

**Trust but Verify** is a classic security concept that emphasizes the need for continuous validation—even when access or actions are initially trusted.

Originating from a Russian proverb popularized during Cold War-era arms control negotiations, the phrase has since been widely adopted in cybersecurity. It reflects a **cautious mindset**: even trusted users, systems, or processes should undergo **ongoing checks** to ensure they behave as expected.

🧠 **CISSP Insight**: This principle acts as a **bridge between traditional perimeter-based security and Zero Trust**, emphasizing the importance of **monitoring**, **auditing**, and **continuous assurance**.

#### Core Concept

- **Trust**: Granting access based on identity, role, or past behavior.
- **Verify**: Constantly monitor and reassess that trust is still valid.

This principle is vital for detecting **insider threats**, **credential compromise**, and **policy drift** in long-running systems.

#### Examples in Security Design

| Scenario                               | Trust                     | Verification Mechanism                      |
|----------------------------------------|---------------------------|---------------------------------------------|
| Employee with VPN access               | Role-based access granted | Session logs, MFA challenges                |
| Cloud admin account                    | Admin privileges assigned | Activity monitoring, audit trails           |
| Signed application                     | Trusted publisher         | Runtime behavior monitoring, hash checking  |
| Internal system-to-system communication| Whitelisted IP or token   | Mutual TLS, anomaly detection               |

#### Mechanisms to Implement “Trust but Verify”

- **Audit Logs**: Track who accessed what, when, and how.
- **Anomaly Detection**: Monitor for behavior deviating from baselines.
- **Multi-Factor Authentication (MFA)**: Even trusted users re-authenticate.
- **Just-In-Time (JIT) Access**: Grant time-limited privileges.
- **Behavioral Analytics (UEBA)**: Detect suspicious user actions.

🚨 **CISSP Exam Tip**: Trust but verify is key to **defense-in-depth**. It complements Zero Trust, not replaces it.

#### Comparison: Trust but Verify vs. Zero Trust

| Principle           | Focus                                       | Default Stance             |
|---------------------|---------------------------------------------|-----------------------------|
| Trust but Verify    | Validate trust continuously                 | Trust initially, then verify|
| Zero Trust          | Deny by default, trust no one automatically | Verify before trusting      |

📌 While “Trust but Verify” assumes **initial trust** with ongoing validation, **Zero Trust** removes initial assumptions altogether.

#### Summary

The **Trust but Verify** principle helps maintain **security assurance** by requiring:

- Continuous monitoring
- Verification of behavior and access
- Reevaluation of roles and permissions

| Key Aspect              | Summary                                                        |
|--------------------------|----------------------------------------------------------------|
| Principle                | Trust must be earned and revalidated, not assumed permanently |
| Use Case                 | Ongoing verification for privileged users or critical systems  |
| Tools & Techniques       | Logging, monitoring, anomaly detection, MFA, JIT access        |
| CISSP Relevance          | Reinforces principles of least privilege and accountability    |

### Privacy by Design (PbD)

**Privacy by Design (PbD)** is a proactive security framework that integrates **privacy protections into the design and architecture** of systems and business processes from the outset—not after deployment.

Originally developed by Dr. Ann Cavoukian, former Information & Privacy Commissioner of Ontario, PbD is now recognized globally, including by the **EU GDPR** and many **international privacy frameworks**.

🛡️ **CISSP Exam Tip**: Know that PbD ensures **privacy is a core design element**—not an afterthought. It's a shift from reactive compliance to proactive design.

#### Key Concept

- Build systems that inherently **respect and protect privacy**.
- Avoid “bolting on” privacy controls after deployment.
- Focus on **data minimization**, **user consent**, and **transparency**.

#### 7 Foundational Principles of Privacy by Design

| Principle                                | Description                                                                 |
|------------------------------------------|-----------------------------------------------------------------------------|
| Proactive not Reactive; Preventative not Remedial | Anticipate and prevent privacy invasions before they happen.               |
| Privacy as the Default Setting           | Personal data is automatically protected without user action.              |
| Privacy Embedded into Design             | Privacy is a core part of systems, not a feature added later.              |
| Full Functionality — Positive-Sum        | Avoid trade-offs; support both privacy and business goals (not zero-sum).  |
| End-to-End Security — Lifecycle Protection| Secure data from collection through deletion.                              |
| Visibility and Transparency              | Operations are visible to users and stakeholders for accountability.       |
| Respect for User Privacy                 | Offer strong privacy defaults, notice, and user-centric options.           |

🧠 **Exam Insight**: PbD is **not only about technical measures**—it includes **policy, governance, and culture**.

#### Global Privacy Standard (GPS)

The **Global Privacy Standard (GPS)** is an international agreement promoting **consistency in privacy expectations and protections**.

- Built on PbD principles.
- Used to **harmonize privacy practices** across different jurisdictions.
- Supports cross-border data transfers under consistent privacy safeguards.

📌 Think of GPS as a **privacy alignment framework**—especially critical in global enterprises operating across countries with varying laws.

#### PbD in System Architecture

PbD is applied by:

- Designing systems to **collect only necessary data** (data minimization).
- Using **pseudonymization** or **encryption** to protect stored/transmitted data.
- Providing clear **user consent flows** and **privacy notices**.
- Embedding **logging**, **auditing**, and **privacy-impact assessments (PIAs)**.

#### Examples of PbD Implementation

| Scenario                   | PbD Implementation Example                                |
|----------------------------|-----------------------------------------------------------|
| Web Application             | Opt-in data collection, no tracking without consent       |
| Health System               | Pseudonymized records for research use                   |
| Mobile App                 | Permissions-based access to device resources              |
| Cloud Storage              | End-to-end encryption and user-controlled data access     |

#### Summary

**Privacy by Design** ensures that privacy is **engineered into the system**—not added after the fact.

| Key Concept            | Summary                                                                  |
|------------------------|--------------------------------------------------------------------------|
| Philosophy             | Embed privacy in design, not post-implementation                        |
| Core Values            | Transparency, control, user consent, and full lifecycle security         |
| Standards              | 7 foundational principles and Global Privacy Standard                    |
| CISSP Relevance        | Applies to SDLC, risk management, privacy regulations, and system design |

### Secure Access Service Edge (SASE)

**Secure Access Service Edge (SASE)** is a modern security architecture that combines **networking and security functions** into a unified, cloud-delivered service. Introduced by Gartner in 2019, SASE addresses the shift from traditional perimeter-based models to **distributed, cloud-native, and mobile environments**.

🧠 **CISSP Insight**: SASE reflects the need for **identity-driven, cloud-friendly security**, enabling secure access regardless of location or device.

#### Core Characteristics

SASE integrates the following services:

- **SD-WAN (Software-Defined WAN)** for intelligent routing
- **Zero Trust Network Access (ZTNA)** for identity-based access control
- **Cloud Access Security Broker (CASB)** for cloud application monitoring
- **Firewall as a Service (FWaaS)** for perimeter defense in the cloud
- **Secure Web Gateway (SWG)** to protect user internet access

These services are delivered **as-a-service from the cloud**, allowing consistent security enforcement and user access policies from any location.

#### Cloud-Native and Identity-Centric

SASE emphasizes:

- **Cloud-Native**: Services are designed to scale elastically with demand, removing reliance on on-premises hardware.
- **Identity-Centric**: Access is based on **user identity**, **device posture**, **context**, and **risk level**—not IP address or physical location.

📌 This aligns with **Zero Trust** principles and supports **remote work, BYOD, and hybrid cloud** environments.

| Traditional Network Perimeter | SASE Architecture                        |
|-------------------------------|------------------------------------------|
| Centralized, static           | Distributed, dynamic                     |
| IP-/location-based control    | Identity-/context-based control          |
| Appliance-based security      | Cloud-delivered security services        |

#### ZTNA, Edge Computing, Monitoring

##### Zero Trust Network Access (ZTNA)
- Replaces VPNs by providing **granular, identity-based access** to specific applications.
- Enforces least privilege and **never trusts by default**.
- Continuously verifies user, device, and context.

##### Edge Computing
- Processing is moved closer to the user/device (the “edge”), reducing latency and improving performance.
- SASE nodes are placed at global edge locations for optimized access and localized policy enforcement.

##### Continuous Monitoring and Analytics
- SASE includes **real-time monitoring**, **threat detection**, and **policy enforcement**.
- Integration with **SIEMs**, **SOAR**, and **UEBA** provides dynamic risk-based access decisions.

#### Benefits of SASE

| Benefit                       | Description                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| Scalability                   | Elastic cloud infrastructure supports global, growing organizations         |
| Unified Security              | Consolidates multiple functions under a single vendor                      |
| Consistent Policy Enforcement | Same security rules regardless of user location or device                  |
| Improved Performance          | Low-latency routing and edge optimization                                  |
| Cost Efficiency               | Reduces the need for multiple on-prem security appliances                   |

#### Summary

**SASE** represents a major shift in enterprise security architecture by **merging network and security** into a cloud-delivered, identity-driven model.

| Feature           | Summary                                                                 |
|-------------------|-------------------------------------------------------------------------|
| Architecture       | Cloud-native, distributed, scalable                                    |
| Security Model     | Based on Zero Trust principles                                          |
| Key Components     | ZTNA, CASB, FWaaS, SWG, SD-WAN                                         |
| Benefits           | Unified control, reduced complexity, enhanced remote security          |
| CISSP Relevance    | Aligns with modern enterprise challenges (remote work, cloud-first)     |

## Techniques for Ensuring CIA

Maintaining **Confidentiality, Integrity, and Availability (CIA)** is a foundational goal in information security. To ensure CIA, security architects apply **system design techniques** that control how software and processes behave and interact with resources. These principles are implemented through controls like **confinement**, **bounds**, and **isolation**, and reinforced using **access control** models and **trust/assurance** frameworks.

### Confinement

**Confinement** (also known as **sandboxing**) is the practice of **restricting a process's ability to access memory and system resources**.

- The process is only allowed to interact with **authorized memory locations** or resources.
- Any attempt to exceed these boundaries is denied, logged, and potentially terminated.

🛡️ Confinement is an **application of the Principle of Least Privilege (PoLP)**—each process can access only what it absolutely needs.

📌 **Implementation Examples**:
- OS-level process isolation
- Security services like **Sandboxie**
- Virtualization solutions (e.g., VMware, VirtualBox)

🧠 **CISSP Tip**: Know that confinement is enforced at the OS level and is used to prevent **data leakage** and **unauthorized access**.

### Bounds

**Bounds** define the **limits of authority** for a process or subject in a system.

- A **bound** represents the **maximum scope of access** a subject can have—what it can read, write, or execute.
- Operating systems use bounds to allocate logical or physical memory segments to processes.

| Term       | Description                                                       |
|------------|-------------------------------------------------------------------|
| Logical Bounds | Limits enforced through OS mechanisms in shared memory spaces     |
| Physical Bounds| Memory segments physically separated (e.g., hardware isolation)   |

📌 **CISSP Insight**: Bounds are set based on the **process’s authority level** (e.g., user mode vs kernel mode) and enforced by the OS.

### Isolation

**Isolation** ensures that a process executes in an environment where **its operations do not affect other processes**.

- Achieved through enforcing **confinement and bounds**.
- Prevents both **accidental interference** and **intentional exploitation**.

Benefits of Isolation:
- Allows one process to fail without compromising the entire system.
- Protects the **operating environment**, **kernel**, and other applications.

📌 Isolation is the **foundation of process security** and supports features like **fail-soft systems** and **fault containment**.

| Mechanism      | Purpose                                |
|----------------|----------------------------------------|
| Hardware isolation | Prevent physical memory overlap     |
| OS-level isolation | Prevent cross-process interference  |
| Virtualization  | Sandboxes entire OS environments       |

### Access Controls

**Access control** ensures that **only authorized subjects can access specific objects**, and only in approved ways.

Access is governed by **rules or policies**, and evaluated by the **access control system**.

Common Models:
- **DAC (Discretionary Access Control)**: Owner sets permissions.
- **MAC (Mandatory Access Control)**: Based on sensitivity labels (e.g., Top Secret).
- **RBAC (Role-Based Access Control)**: Based on assigned roles.
- **ABAC (Attribute-Based Access Control)**: Based on attributes of user, resource, and environment.

🧠 **CISSP Exam Tip**: Access controls enforce the CIA triad by **limiting what can be done, by whom, and under what circumstances**.

### Trust and Assurance

**Trust**: The belief that a system will enforce its security policy reliably.

**Assurance**: The **confidence that security measures are implemented correctly** and will function as intended.

Key Points:
- Trust is built by implementing **security mechanisms**.
- Assurance is measured via **testing, validation, and certifications** (e.g., Common Criteria, EAL levels).

🛠️ **Assurance Maintenance**:
- **Revalidating** after system changes (e.g., updates, breaches)
- Following best practices in **patch management**, **configuration management**, and **change control**

| Term      | Description                                                          |
|-----------|----------------------------------------------------------------------|
| Trust     | Presence of security functionality                                   |
| Assurance | Confidence in the effectiveness and reliability of that functionality|

📌 **CISSP Insight**: Assurance must be continually maintained and reviewed—especially after system changes.

### Summary

| Technique     | Purpose                                                       |
|---------------|---------------------------------------------------------------|
| Confinement   | Limits a process to its designated memory/resource space      |
| Bounds        | Defines maximum allowable access for subjects or processes    |
| Isolation     | Prevents one process from interfering with another            |
| Access Control| Enforces who can access what, when, and how                   |
| Trust & Assurance | Evaluates the reliability and strength of security features |

These techniques **collectively reinforce CIA** and are critical to designing secure, stable, and enforceable systems.

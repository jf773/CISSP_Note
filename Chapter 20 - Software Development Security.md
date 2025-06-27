# Chapter 20: Software Development Security

- [Introducing Systems Development Controls](#introducing-systems-development-controls)
  - [Software Development](#software-development)
  - [Systems Development Life Cycle](#systems-development-life-cycle)
  - [Life Cycle Models](#life-cycle-models)
  - [Gantt Charts and PERT](#gantt-charts-and-pert)
  - [Change and Configuration Management](#change-and-configuration-management)
  - [The DevOps Approach](#the-devops-approach)
  - [Application Programming Interfaces](#application-programming-interfaces)
  - [Software Testing](#software-testing)
  - [Code Repositories](#code-repositories)
  - [Service-Level Agreements](#service-level-agreements)
  - [Third-Party Software Acquisition](#third-party-software-acquisition)
- [Establishing Databases and Data Warehousing](#establishing-databases-and-data-warehousing)
  - [Database Management System Architecture](#database-management-system-architecture)
  - [Database Transactions](#database-transactions)
  - [Security for Multilevel Databases](#security-for-multilevel-databases)
  - [Open Database Connectivity](#open-database-connectivity)
  - [NoSQL](#nosql)
- [Storage Threats](#storage-threats)
- [Understanding Knowledge-Based Systems](#understanding-knowledge-based-systems)
  - [Expert Systems](#expert-systems)
  - [Machine Learning](#machine-learning)
  - [Neural Networks](#neural-networks)
- [Summary](#summary)

## Introducing Systems Development Controls
* Building security in early 🛠️ is **cheaper** and **stronger** than bolting it on later.  
* Controls span policies, standards, secure coding, rigorous testing, and change/configuration management.

### Software Development
Security touch-points exist in **all** SDLC phases—requirements ➝ design ➝ coding ➝ testing ➝ deployment ➝ maintenance.

#### Programming Languages
| Language Category | Examples | Security Pros | Security Cons |
|-------------------|----------|---------------|---------------|
| **Compiled** | C, C++, Go, Rust, Java (.class files) | 📦 Binary harder to tamper; faster run-time; can enforce memory safety (Rust) | Reverse-engineering possible; vulnerable if compiler/flags mis-used |
| **Interpreted** | Python, Perl, Ruby, JavaScript | Source visible—peer review friendly 😎 | Source visible—easy to alter; slower |
| **Hybrid / Byte-code** | Java (JVM), .NET (CLR) | Portability, runtime sandbox | Byte-code still reversible; JIT introduces attack surface |

##### Key Terms  
* **Machine Language** – raw CPU op-codes.  
* **Assembly** – mnemonic shorthand for machine language.  
* **High-Level** – human-friendly; relies on compilers or interpreters.  
* **Obfuscation** – intentionally makes compiled code harder to reverse.

#### Libraries
* Reusable code (open-source or proprietary).  
* Risks: inherited vulnerabilities (e.g., **Heartbleed** in OpenSSL), supply-chain attacks.  
* Mitigation: SBOM 📝, routine patching, dependency scanning (SCA).

#### Development Tool Sets
* **IDE** – Integrated Development Environment (e.g., Visual Studio, IntelliJ, RStudio) consolidates edit + debug + build.  
* Secure IDE config disables dangerous plugins, enforces code signing, runs SAST.

#### Object-Oriented Programming (OOP)
| Concept | Brief | Security Angle |
|---------|-------|----------------|
| Class / Object | Blueprint vs. instance | Encapsulation hides data ↔ reduces attack surface. |
| Inheritance | Sub-classes gain parent traits | Follows **substitution** (Liskov) principle. |
| Polymorphism | Same message ⇒ different behaviors | Avoid abuse leading to unexpected privilege use. |
| Cohesion (high good) | Similar purpose methods | Simplifies auditing 🕵️‍♂️ |
| Coupling (low good) | Few external dependencies | Limits cascading failures. |

#### Assurance
* Confidence that controls **correctly implement** policy over the system’s lifetime.  
* Common Criteria 🔐 provides Evaluation Assurance Levels (EALs) 1 – 7.

#### Avoiding and Mitigating System Failure
##### Input Validation
* Server-side, whitelist, boundary & limit checks, canonicalization.  
* Reject or escape 🚫 injected meta-characters.

##### Authentication and Session Management
* Leverage enterprise IAM (SSO, MFA).  
* Long, random session tokens; timeout & re-auth.

##### Error Handling
* User-facing ➝ generic.  
* Detailed stack-traces only in protected logs.

##### Logging
* Centralized, write-once, clock-synced.  
* OWASP recommends logging auth failures, access control errors, tampering, TLS issues, etc.

##### Fail-Secure vs. Fail-Open
| Mode | Description | Typical Use |
|------|-------------|-------------|
| **Fail-Secure** 🔒 | Deny all on failure; preserve confidentiality/integrity | Most security controls |
| **Fail-Open** 🚦 | Allow access to maintain availability | Non-critical guard devices (rare) |

### Systems Development Life Cycle

#### 🛡️ Overview  
Security delivers the greatest ROI when it is **planned, embedded, and managed across every SDLC phase**.  Life-cycle models (Waterfall, Agile, Spiral, etc.) provide the project-management scaffolding that keeps development on target, embeds secure-coding best practices, and aligns with CISSP exam objectives.

#### Core Activities at a Glance  

| SDLC Activity | Purpose | Security Focus 🤔 |
|---------------|---------|-------------------|
| Conceptual definition | Draft project’s high-level purpose & scope | Identify **data classifications** & preliminary protection goals |
| Functional requirements determination | Document what the system must do | Bake in confidentiality, integrity, availability (CIA) requirements |
| Control specifications development | Translate security needs into concrete controls | Access controls, encryption, auditing, fault-tolerance |
| Design review | Validate architecture before coding | Ensure design meets functional & security specs |
| Coding | Implement design using secure-coding principles | Follow least privilege, input validation, error handling |
| Code review walk-through | Peer review code for defects & vulns | Detect logic errors, insecure APIs, poor crypto use |
| System test review | Validate system operates & secures as intended | Functional, security, regression, & **UAT** testing |
| Maintenance & change management | Sustain secure operations post-deployment | Patch mgmt, incident response, formal change control |

##### Conceptual Definition  
* Single-paragraph **concept statement** agreed by stakeholders.  
* Establishes project vision, scope, and **initial** (high-level) security requirements.  
* Designers flag **data classifications** & handling standards.

##### Functional Requirements Determination  
* Produces **Functional Requirements Document (FRD)** with:  
  * **Inputs** – data accepted  
  * **Behavior** – business logic / rules  
  * **Outputs** – data produced  
* Must reach stakeholder consensus; used later as **UAT checklist**.

##### Control Specifications Development  
* Proactive design of security controls—never an afterthought!  
* Addresses:  
  * **Access control** (authN/authZ)  
  * **Confidentiality** – crypto, data-at-rest/flight protection  
  * **Integrity & Accountability** – logging, auditing  
  * **Availability** – redundancy, fault tolerance  
* Revisit controls if design changes significantly.

##### Design Review  
* Architects finalize modular design & timelines.  
* **Formal review meeting** ensures alignment with control specs.  
* Security pros validate that design respects CIA & compliance needs.

##### Coding  
* Developers follow **secure-coding standards** (input validation, output encoding, least privilege modules, safe APIs).  
* Aim to minimize vulnerabilities early—cheaper than fixing later.

##### Code Review Walk-Through  
* Scheduled milestone peer reviews.  
* Detects logical flaws, insecure patterns, missing error handling.  
* Promotes knowledge sharing & consistent coding style.

##### System Test Review  
1. **Developer / integration tests** – catch obvious errors.  
2. **Functional tests** – validate requirements.  
3. **Security tests** – penetration, fuzzing, vulnerability scans.  
4. **Regression tests** – confirm updates don’t break existing features.  
5. **User Acceptance Testing (UAT)** – end users verify business fit.  

> 📌 **Deliverable**: Signed test plan & results archive for audit trail.

##### Maintenance and Change Management  
* Continuous operations require:  
  * Routine & emergency maintenance  
  * **Patch & vulnerability management**  
  * Performance / security monitoring  
* All updates funnel through a **formal change-management process** (identification, evaluation, approval, implementation, review) to maintain integrity & compliance.

##### Exam Tips 📖  
* Expect questions on **embedding security early** vs. bolting it on.  
* Know differences between **UAT, regression, and functional testing**.  
* Remember: Change control = protection against **unauthorized modifications**.  
* SDLC activities map tightly to CISSP CBK Domain 8 “Software Development Security”.


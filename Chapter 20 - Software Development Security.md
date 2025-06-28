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

### Life Cycle Models

#### 📚 Overview  
Life-cycle models formalize the **software development life cycle (SDLC)** and embed security into every phase. CISSP Domain 8 expects you to:  

* Recognize major SDLC frameworks and when they fit best.  
* Understand how security activities map into each model.  
* Evaluate maturity frameworks (CMM, SAMM, IDEAL) that rate an organization’s software process capability.  

#### Waterfall Model  

##### Key Characteristics  
* **Sequential / Phase-Gate**: Requirements → Design → Implementation → Verification → Maintenance.  
* **Iterative Waterfall** adds *feedback loops* 🌀 allowing a project to return **one** phase to fix discovered defects.  
* **Verification vs. Validation**:  
  * **Verification** – *Did we build it right?*  
  * **Validation** – *Did we build the right thing?*  

##### Strengths & Weaknesses  

| 👍 Strengths | 👎 Weaknesses |
|-------------|--------------|
| Clear milestones & documentation | Late discovery of defects |
| Suits well-understood, low-change projects | Hard to accommodate changing requirements |
| Easier regulatory compliance audits | Rarely delivers early business value |

#### Spiral Model  

##### Key Characteristics  
* **Barry Boehm (1988)**; a *metamodel* (model of models).  
* Repeats *waterfall cycles* (“loops”) to produce incremental **prototypes (P1, P2, P3)**.  
* Each loop addresses **risk analysis** → engineering → evaluation → planning.  
* Enables **return to planning** for evolving requirements.  

##### Spiral Strengths  
* Early detection/mitigation of high-risk items.  
* Progressive refinement yields usable prototypes sooner.  
* Suited to large, high-risk, evolving systems.

#### Agile Software Development  

##### Agile Manifesto Highlights  
* **Individuals & interactions** over processes/tools.  
* **Working software** over exhaustive docs.  
* **Customer collaboration** over contract negotiation.  
* **Responding to change** over following a rigid plan.  

###### Agile Principles (Condensed)  
Early & continuous delivery, welcome change, frequent releases, daily business-dev collaboration, motivated teams, face-to-face comms, working SW as progress metric, sustainable pace, technical excellence, simplicity, self-organizing teams, regular reflection.

##### Popular Methodologies  

| Methodology | Core Ideas | Security Hooks |
|-------------|-----------|----------------|
| **Scrum** | Daily stand-ups (scrums), 1–4 wk **sprints**, Scrum Master facilitates, deliver shippable product increment each sprint | Integrate **security user stories**, *definition of done* includes security criteria |
| **Kanban** | Continuous flow with WIP limits via Kanban board | **Security tasks/lanes** ensure ongoing hardening |
| **Extreme Programming (XP)** | Pair programming, TDD, continuous integration | Built-in testing supports secure code; pair reviews reduce flaws |
| **Lean / RAD / DSDM / AUP** | Variations focusing on waste reduction or rapid prototyping | Apply **secure-coding** checklists in rapid cycles |

#### Integrated Product Teams  

* **DoD concept (1995)** – cross-functional teams (dev, ops, security, business) collaborate continuously through the product life cycle.  
* Promotes **parallel decisions** and early security integration across disciplines.

#### Scaled Agile Framework (SAFe)  

##### Configuration Levels  

| Level | Scope | Notes |
|-------|-------|-------|
| **Essential** | Foundation; **Agile Release Train (ART)** delivers Program Increment (8-12 wks) | Traditional Scrum & XP at team level |
| **Large Solution** | Coordinates multiple ARTs | Extra roles/artifacts for system-of-systems |
| **Portfolio** | Aligns strategy & investment via **Lean Portfolio Management** | Uses **Epics**, **Value Streams** |
| **Full** | Combines all above; supports enterprise-wide agility | For hundreds/thousands of practitioners |

##### 10 SAFe Principles (memory tip: **EAST CALM-O!** 🧭)  
1. **E**conomic view  
2. **A**pply systems thinking  
3. **S**tate variability / preserve options  
4. **T**est & build incrementally  
5. **C**heckpoints via objective milestones  
6. **A**llow value flow  
7. **L**ock cadence & synchronize  
8. **M**otivate knowledge workers  
9. **D**ecentralize decisions *(-O represents Organize around value)*  
10. **O**rganize around value  

#### Capability Maturity Model (CMM) & CMM Integration (CMMI)  

| Level | Name (CMM) | Primary Focus | Security Implications |
|-------|------------|---------------|-----------------------|
| **1** | Initial | Ad-hoc / chaotic processes | Unpredictable quality, high risk |
| **2** | Repeatable | Basic PM & reuse | Documented config mgmt, QA points |
| **3** | Defined | Organization-wide standards | Security policy integration begins |
| **4** | Managed ★ (CMMI: *Quantitatively Managed*) | Metrics & quantitative control | Measure defect density, vuln trends |
| **5** | Optimizing | Continuous improvement | Proactive defect prevention & threat intelligence loops |

> 🗝️ **Difference**: CMM targets *isolated* processes; **CMMI** focuses on *integrating* them across the org.

#### Software Assurance Maturity Model (SAMM) – OWASP  

| Business Function | Security Practices |
|-------------------|--------------------|
| **Governance** | Strategy & Metrics, Policy & Compliance, Education & Guidance |
| **Design** | Threat Modeling, Security Requirements, Security Architecture |
| **Implementation** | Secure Build, Secure Deployment, Defect Management |
| **Verification** | Architecture Assessment, Requirements-Driven Testing, Security Testing |
| **Operations** | Incident Mgmt, Environment Mgmt, Operational Mgmt |

*Assesses maturity & guides roadmap for weaving security activities into SDLC.*

#### IDEAL Model  

| Phase | Purpose |
|-------|---------|
| **Initiating** | Identify business drivers & establish sponsorship |
| **Diagnosing** | Assess current state & recommend improvements |
| **Establishing** | Develop actionable work plan |
| **Acting** | Implement, test, refine solutions |
| **Learning** | Analyze results & feed improvements back |

> 👁️‍🗨️ **Mnemonic** to recall SW-CMM & IDEAL pairings:  
> “*I… I, Dr. Ed, am lo(w).*”  
> *II DR ED AM LO* → **Initiating, Diagnosing, Establishing, Acting, Learning** (IDEAL) vs. **Initial, Repeatable, Defined, Managed, Optimizing** (CMM).

#### Model Comparison Table  

| Model | Style | Handles Change? | Security Integration Point |
|-------|-------|-----------------|----------------------------|
| Waterfall | Sequential | Poor (feedback only one phase) | Control specs after requirements |
| Spiral | Iterative risk-driven | Excellent (each loop reassesses) | Risk analysis per loop |
| Agile / Scrum | Incremental, time-boxed | Excellent (backlog reprioritized) | Security stories per sprint, CI/CD tests |
| SAFe | Agile @ scale | Excellent (ART PI planning) | Security built into Definition of Done, Communities of Practice |
| CMMI / IDEAL | *Process maturity* frameworks | N/A (assess org, not dev style) | Security maturity increases with levels |
| SAMM | *Security maturity* framework | N/A | Directly maps security activities to SDLC functions |

#### CISSP Exam Nuggets 💡  
* Waterfall vs. Spiral vs. Agile = know **change management & risk handling** differences.  
* CMM/CMMI maturity **levels & keywords** are test favorites.  
* Agile security = embed **user stories, threat modeling, automated testing** into each sprint.  
* SAFe adds **Essential ➜ Full** layers; remember **ART** & **Program Increments**.  
* SAMM & IDEAL appear less often but reinforce **continuous improvement** concept.


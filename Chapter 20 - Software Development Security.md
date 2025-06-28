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
* **Sequential / Phase-Gate**: System Requirements → Software Requirements → Preliminary Design → Detailed Design → Code and Debug → Testing → Operations and Maintenance  
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

### Gantt Charts and PERT

#### 📚 Overview  
Project‐scheduling tools visualize **tasks, durations, dependencies, and resources** to keep complex software initiatives on track. Two exam-relevant techniques are **Gantt charts** and the **Program Evaluation Review Technique (PERT)**.  
*Expect questions on when to use each, interpretation of diagrams, and basic calculations (e.g., PERT’s expected time & standard deviation).* ⚠️

#### Gantt Charts  

##### Concept  
* Horizontal **bar chart** mapping tasks (rows) against a **timeline** (columns).  
* Each bar’s length = task duration; position = start/finish dates.  
* **Milestones** shown as diamonds or special markers.  
* **Dependencies** may appear as connecting arrows.  

###### Advantages  
1. **Intuitive visualization** – stakeholders “see” progress quickly.  
2. **Resource coordination** – overlaps reveal resource conflicts.  
3. **Baseline vs. Actual** – track schedule variance 📊.  

###### Limitations  
* Harder to portray **complex task relationships** (multiple predecessors).  
* Can become cluttered on very large projects.  

#### Program Evaluation Review Technique (PERT)  

##### Concept  
* **Network diagram** illustrating **task sequence & dependencies**.  
* Nodes = milestones/events; arrows = tasks (activities).  
* Incorporates *probabilistic estimates* to address **time uncertainty** ⏳.  

###### Three-Point Estimate  
For each activity, collect:  
* **O** – Optimistic time (best case)  
* **M** – Most likely time  
* **P** – Pessimistic time (worst case)  

> **Expected Time (TE)**  
> \( TE = \dfrac{O + 4M + P}{6} \)

> **Standard Deviation (σ)**  
> \( σ = \dfrac{P - O}{6} \)

*Used to quantify schedule risk and inform buffers.*

###### Critical Path  
* **Longest duration path** through the network.  
* **Slack/float** = time an activity can slip without delaying project.  
* Any delay on critical path → entire project slips 🚨.  

#### Comparison Table  

| Feature | **Gantt Chart** | **PERT** |
|---------|-----------------|----------|
| Primary View | Timeline bars | Network diagram |
| Best For | Visual progress & resource allocation | Analyzing task **sequence**, **uncertainty**, critical path |
| Time Estimate | Deterministic (single duration) | Probabilistic (O, M, P) |
| Risk Metric | Schedule variance tracking | σ & expected time compute **schedule risk** |
| Complexity Handling | Moderate; can clutter | Excels at complex dependencies |
| Typical Usage | Status reporting ✔️ | Planning & what-if analysis ✔️ |

#### CISSP Tips 💡  

* **Memorize** the PERT formulas for TE and σ – they appear on practice exams.  
* Remember: **Gantt = timeline**, **PERT = network + probability**.  
* On the exam, if the question stresses **resource conflicts** or **communicating schedule to execs → Gantt**. If it focuses on **critical path, dependencies, or risk buffer → PERT**.  

### Change and Configuration Management

#### 🗺️ Big Picture  
After code is promoted to production, **new features, bug fixes, and maintenance** are inevitable.  
*Uncontrolled changes ➡️ instability, security holes, audit failures.*  
CISSP candidates must know **process disciplines** that maintain integrity, availability, and traceability.

#### Change Management 🙋‍♀️

##### Purpose  
* Provide an **organized, auditable framework** for altering production systems.  
* Minimize risk by ensuring **authorization, testing, documentation, and rollback** are integral parts of every change.

##### Three Core Components  

| Component | Key Activities | Security Impact |
|-----------|----------------|-----------------|
| **Request Control** | • Users/devs submit formal change requests 📝 <br>• Management performs cost/benefit & prioritization| Ensures *business justification* and *risk evaluation*. |
| **Change Control** | • Devs reproduce issue or build feature <br>• Code, configs, or infrastructure changes crafted & **tested in non-prod** <br>• Quality gates + peer review | Prevents unauthorized or poorly designed changes from reaching production. |
| **Release Control** | • Final approval ✔️ <br>• **Acceptance testing** by stakeholders <br>• Verify no leftover debug code/backdoors <br>• Deploy via controlled mechanism (CMDB updated) | Guarantees only vetted versions hit live environment, preserving **CIA**. |

> 💡 **Exam tip:** Know that *file integrity monitoring* + change tickets 🎫 = rapid detection of unauthorized modifications.

#### Configuration Management 🗄️

> **Goal:** Maintain **consistent, secure, and known** software states across the enterprise.

##### Four Pillars  

1. **Configuration Identification**  
   *Inventory & baseline* all software/firmware versions and their locations.

2. **Configuration Control**  
   Enforce that **only approved packages** are deployed; ties directly to change control workflow.

3. **Configuration Status Accounting**  
   Continuous **record-keeping** of every authorized change.

4. **Configuration Audit**  
   Periodic review 🔍 verifying production equals the documented baseline; uncovers rogue changes.

#### Change vs. Configuration Management—Quick View  

| Aspect | **Change Mgmt.** | **Configuration Mgmt.** |
|--------|------------------|-------------------------|
| Focus | *Process* of modifying systems | *State* of systems post-change |
| Trigger | New requirement, defect, or enhancement request | Detection of drift from baseline |
| Output | Approved change packages, updated tickets | Updated baselines, CMDB entries |
| Key Control | Request / Change / Release cycle | Identification / Control / Accounting / Audit |

#### Security Use Case Example  

*File Integrity Monitoring (FIM) System*  
1. FIM detects hash change on `/opt/app/bin/login` 😱  
2. SOC correlates with **change ticket #1234**.  
3. If **match** → event logged as legitimate.  
4. If **no correlation** → escalate for IR; possible malware/tampering.  

**Result:** Admin noise reduced, alerts become actionable.

#### CISSP Exam Nuggets 🎯  

* Expect definitions of **Request, Change, Release** control.  
* Differentiate **SCM** components from change management stages.  
* Know that both processes feed evidence into **audits, investigations, troubleshooting, and compliance**.  
* Understand how tools (FIM, CMDB, version control) support these frameworks.  

### DevOps Approach

#### Overview
DevOps unifies **software development**, **quality assurance**, and **IT operations** to deliver secure, high-quality software **rapidly** and **reliably**.

- Breaks down organizational silos 🤝  
- Emphasizes automation, collaboration, continuous feedback  
- Aligns with **Agile** values and principles  

#### Key Characteristics

| Characteristic | Traditional Model | DevOps Model |
| :-- | :-- | :-- |
| Team Structure | Separate Dev / QA / Ops silos | Cross-functional, collaborative |
| Deployment Frequency | Quarterly / annual | Multiple per day (CI/CD) |
| Feedback Loops | Slow, manual | Rapid, automated 🔄 |
| Change Size | Large releases | Small, incremental |
| Automation | Limited | Extensive across pipeline ⚙️ |
| Culture | Blame & hand-offs | Shared responsibility |
| Metrics | Uptime, post-release defects | Lead time, MTTR, deployment success |

#### DevOps Pipeline Stages

1. **Plan** – Capture requirements; update backlog.  
2. **Code** – Developers commit to shared repo.  
3. **Build** – Automated compile & unit tests validate commits.  
4. **Test** – Automated functional, integration, performance, and security tests.  
5. **Release** – Package artifacts; trigger approvals.  
6. **Deploy** – Automated rollout to production (blue-green, canary, etc.).  
7. **Operate** – Monitor, log, and measure KPIs.  
8. **Monitor / Feedback** – Telemetry feeds improvements back to **Plan**.

#### Continuous Integration / Continuous Delivery

| Term | Definition | Primary Benefit |
| :-- | :-- | :-- |
| Continuous Integration (CI) | Frequent merges to main branch with automated builds/tests | Detect integration issues early 🐛 |
| Continuous Delivery (CD) | Automated release to staging environments | Faster feedback from stakeholders |
| Continuous Deployment | Automatic push to production after tests pass | On-demand, low-risk releases 🚀 |

#### DevSecOps (Security in DevOps)

Security is integrated into **every** pipeline stage—**shift-left**:

- **Security as Code** – policies & controls codified in pipeline scripts.  
- **Automated Scanning** – SAST, DAST, dependency, container, IaC scans 🛡️  
- **Continuous Compliance** – real-time evidence collection & auditing.  

> **Goal:** Match DevOps speed **without** sacrificing security.

#### Automation & Tool Categories

| Function | Representative Tools (examples) |
| :-- | :-- |
| Source Control | Git, GitHub, GitLab |
| CI Servers | Jenkins, GitHub Actions, GitLab CI |
| Containerization | Docker, Podman |
| Orchestration | Kubernetes, OpenShift |
| Infrastructure as Code | Terraform, AWS CloudFormation |
| Configuration Management | Ansible, Puppet, Chef |
| Monitoring / Observability | Prometheus, Grafana, ELK stack |
| Security Scanning | Snyk, Trivy, OWASP ZAP, SonarQube |

*(Know categories, not product specifics, for the exam.)*

#### Best Practices

- **Culture of Collaboration** – blameless post-mortems & shared KPIs.  
- **Automation First** – script manual steps to reduce human error.  
- **Small, Reversible Changes** – reduce blast radius & enable quick rollback.  
- **Version Everything** – code, infrastructure, configurations.  
- **Monitor & Measure** – lead time, deployment frequency, change failure rate, MTTR.  
- **Embed Security Early** – automated scans in CI, policy-as-code.  

#### Exam Tips

- Differentiate **DevOps** from traditional siloed models.  
- Understand CI/CD flow and its **security touch points**.  
- Recognize **DevSecOps** and “shift-left” security concepts.  
- Memorize key **metrics**: lead time, deployment frequency, MTTR, change failure rate.  
- Recall categories of automation tools and their roles in the pipeline.

### Application Programming Interfaces

#### Introduction
Modern web applications rarely operate in isolation. Instead, they **interoperate** with other services (e-commerce 🛒, social media 📣, shipping 📦, etc.) via **Application Programming Interfaces (APIs)**. APIs expose backend functions directly to other applications, bypassing traditional web UIs through structured requests (e.g., REST, GraphQL, SOAP).

#### Common API Operations (Example: Social Media)
| Operation | Purpose |
| :-- | :-- |
| `PostStatus` | Publish user content |
| `FollowUser` | Subscribe to another user’s updates |
| `UnfollowUser` | Remove subscription |
| `LikePost` / `FavoritePost` | Express approval for content |

#### Security Considerations

##### ⚙️ Authentication & Authorization
- **Public APIs** – read-only, no auth required (e.g., weather).  
- **Private / Partner APIs** – require **API keys** or OAuth tokens.  
- **User-Scoped APIs** – must validate user identity & permissions on *every* call.

> 🔑 **API keys** act like passwords—store securely, transmit only over **encrypted channels (TLS)**.

##### 🔄 Input Validation & Sanitization
- Treat parameters in API calls like any other untrusted input.  
- Protect against **SQLi, XSS, command injection**.

##### 🔒 Transport Security
- Enforce HTTPS/TLS for *all* API traffic.  
- Use modern ciphers; disable weak protocols (SSL 3.0, TLS <1.2).

##### 📈 Rate Limiting & Throttling
- Prevent abuse / DoS via quotas, burst limits, CAPTCHAs.

##### 📝 Logging & Monitoring
- Record request metadata, auth results, error codes.  
- Monitor for anomalous patterns (e.g., spikes, invalid auth attempts).

#### API Testing & Assessment

| Testing Method | Description | Tools / Techniques |
| :-- | :-- | :-- |
| Functional Testing | Verify intended outputs for valid inputs | Postman, unit tests |
| Security (Pen-) Testing | Identify vulnerabilities (auth bypass, injection, IDOR) | OWASP ZAP, Burp Suite |
| Fuzzing | Send random / malformed data to observe failures | Boofuzz, Peach |
| Static Analysis (SAST) | Evaluate source code for insecure patterns | SonarQube, Semgrep |
| Dynamic Analysis (DAST) | Scan running service for vulnerabilities | OWASP ZAP, Nikto |

#### curl and Direct API Interaction
- **curl** is a command-line HTTP client used for *testing* and *exploiting* APIs.  
- Example POST request:

      curl -H "Content-Type: application/json" \
           -X POST \
           -d '{"week":10,"hrv":80,"sleephrs":9,"sleepquality":2,"stress":3,"paxid":1}' \
           https://prod.myapi.com/v1

  - `-H` sets headers  
  - `-X` specifies method  
  - `-d` provides JSON payload

- Attackers may use curl (or similar tools) to automate brute force or injection attacks; defenders must **log, detect, and block** suspicious patterns.

#### API Security Best Practices ✅
- Enforce **least privilege** on API tokens.  
- Implement **token rotation** and revocation mechanisms.  
- Use **input schemas** (JSON Schema, OpenAPI) for strict validation.  
- Adopt **zero-trust** approach—never assume internal traffic is safe.  
- Perform **regular security assessments** & integrate into CI/CD.  
- Publish **versioned endpoints** and deprecate insecure versions.  
- Include **detailed rate-limit headers** to aid client compliance.

#### Exam Pointers 🎯
- Understand **API key** security and the risks of leaked keys.  
- Recall **authentication vs. authorization** requirements for APIs.  
- Recognize **curl** as a direct interaction tool (testing & exploiting).  
- Identify security controls: TLS, rate limiting, input validation, logging.  
- Know the necessity of **continuous security testing** in DevSecOps pipelines.

### Software Testing

#### Purpose and Integration in the SDLC
* **Comprehensive testing** is essential for risk analysis 🛡️ and mitigation before internal distribution or public release.
* Design tests **in parallel** with modules to ensure full coverage and pre-defined expected results.
* Incorporate both **use cases** (normal operations) and **misuse cases** (attacker scenarios).

#### Reasonableness Check
* Validates that returned values are **within acceptable bounds**.
  * Example: A human-weight algorithm returning **612 lb** ⇒ fails reasonableness check.

#### Data Handling in Tests
* **Avoid live/production data** in early development to protect confidentiality & integrity.
* Use synthetic or **sanitized datasets** for stress testing and edge-case evaluation.

#### Separation of Duties
| Role | Responsibility | Rationale |
|------|---------------|-----------|
| **Developer** | Write & fix code | Prevents bias in testing |
| **Tester / QA** | Independent functional & security testing | Provides objective evaluation |
| **Security Reviewer** | Validate against security requirements | Ensures compliance & defense |

#### Testing Philosophies
| Approach | Access to Source Code | Focus | Typical Use |
|----------|----------------------|-------|-------------|
| **White-Box** | Full | Internal logic & control flow | Unit tests, code audits |
| **Black-Box** | None | Inputs ↔ Outputs | User acceptance, final validation |
| **Gray-Box** | Limited | Input/output with code insight | Integrated security validation |

#### Security-Focused Testing
* **Static Analysis** (code review) – examines source/binary without execution.
* **Dynamic Analysis** – evaluates running code in real/virtual environments.
* **File Integrity Monitoring** – detects unauthorized changes; integrate with **change-management** workflows to reduce false-positives.

#### Change & Configuration Management Alignment
1. **Request Control** – log and prioritize change requests.
2. **Change Control** – develop, test, and stage updates.
3. **Release Control** – approve, deploy, and verify updates.
4. **Software Configuration Management (SCM)** – version tracking, audits, and rollback capabilities.

#### Documentation and Continuous Improvement
* Maintain **permanent records** of test plans and results.
* Feed lessons learned back into **Agile/DevSecOps pipelines** for iterative enhancement.

##### Key Takeaways ✨
* Early, independent, and methodical testing **reduces vulnerabilities** and project risk.
* Integrate **security testing tools** (SAST, DAST, FIM) into CI/CD.
* Enforce **strict change control** to ensure production integrity and rapid issue resolution.

### Code Repositories

#### ****Central Role in Collaborative Development****
* Act as a **single source of truth** for geographically‐dispersed teams.  
* Provide **version control**, **bug tracking**, **release management**, and **team communication**.  
* Popular platforms ⇒ **GitHub**, **Bitbucket**, **SourceForge** – tightly integrated with tools like **git**.  

#### ****Difference Between Libraries and Repositories****
| Concept | Purpose | Scope |
|---------|---------|-------|
| **Code Library** | Reusable package / module | *Single* function or set of functions |
| **Repository** | End-to-end collaboration platform | Full **projects**, multiple libraries, documentation, CI/CD, issue tracking |

Repositories often *host* and *manage* the distribution of internal or public libraries.

#### ****Security Risks and Access Control****
* **Access Design**  
  * Grant **read** and **write** rights only to **authorized** individuals.  
  * Public-facing projects ⇒ sanitize content before publication.  
* **Over-permissive reads**  ▶︎ leakage of proprietary algorithms, credentials, or trade secrets.  
* **Over-permissive writes** ▶︎ unauthorized code tampering, backdoors, or supply-chain attacks.  

#### ****Sensitive Information Pitfalls****
1. **API Keys**  
   * Keys enable programmatic control over IaaS (AWS, Azure, GCP).  
   * Public exposure ⇢ attacker provisions resources → costs billed to key owner.  
   * Bots continuously scan public repos; detection often within **seconds**.  
2. **Passwords & Secrets**  
   * Embed secrets only via **secure vaults** or environment variables.  
   * Avoid hard-coding database names, internal hostnames, encryption keys.

##### **Mitigation Checklist ✅**
* Enforce **branch protection** and pull-request reviews.
* Employ **pre-commit hooks** & **secret‐scan tools** (e.g., TruffleHog, Git-Secrets).  
* Rotate exposed keys **immediately**; monitor billing dashboards for anomalies.  
* Use **encrypted secret managers** (AWS Secrets Manager, HashiCorp Vault).  
* Audit repository permissions **regularly** — remove stale or unnecessary access.  

### Service-Level Agreements

#### ****Purpose & Scope****
* Formal **commitment** between **service provider** and **customer**.  
* Defines measurable **performance targets** for **data circuits, apps, databases, cloud services, etc.**  
* Protects business continuity by setting expectations and remedies.

#### ****Key Performance Metrics****
| Metric | Description | Typical Target |
|--------|-------------|----------------|
| **System Uptime** | % of total time service is operational | 99.9% – 99.999% |
| **Max Consecutive Downtime** | Longest single outage allowed before breach | 5–15 min |
| **Peak Load Handling** | Max simultaneous transactions / throughput | Defined per service |
| **Average Load** | Normal operating utilization | ≤ 70 % capacity |
| **Failover Time** | Time to switch to redundant resources | < 60 sec |

`Responsibility for diagnostics` — SLA must clearly assign which party investigates and resolves incidents.

#### ****Enforcement & Remedies****
* **Continuous monitoring** of agreed metrics by both parties.  
* Breach triggers **financial credits**, penalty fees, or extended support.  
  * *Example*: >15 min outage ⇒ *one week* circuit fees waived.  
* May stipulate **escalation paths**, incident response timelines, and reporting requirements.

#### ****Best-Practice Checklist ✅****
* Align SLA metrics with **business impact analysis** (BIA) findings.  
* Include **clear definitions** of measurement methods & time windows.  
* Establish **review cadence** to adjust terms for evolving needs.  
* Integrate SLA monitoring dashboards with **alerting & ticketing** systems.  
* Ensure legal counsel reviews **remedy clauses** and liability limits.  

### Third-Party Software Acquisition

#### ****Acquisition Models****
* **Commercial Off-The-Shelf (COTS)** – Org installs & manages software on-prem or in IaaS.  
* **Software as a Service (SaaS)** – Vendor hosts & operates; users access via web/API.  
* **Open-Source Software (OSS)** – Community developed; free to use or embed within other products.  
* **Hybrid Use** – Most enterprises mix COTS, SaaS, & OSS to satisfy varying business demands.  

#### ****Security Responsibilities****
| Model | Org’s Duties | Vendor’s Duties |
|-------|--------------|-----------------|
| **COTS** | Secure config, patch mgmt, hardening, monitoring | Vulnerability disclosure, patch releases |
| **SaaS** | Vendor assessments, account & access mgmt, compliance review | Infra + app security, patching, uptime |
| **OSS** | Code review, integration security, community patch tracking | Community maintains code, issues fixes |

**Shared-responsibility principle:** Regardless of model, both parties carry some portion of the security burden.

#### ****Due Diligence & Monitoring****
* Evaluate vendor security posture via **audits, SOC reports, pen-tests**.  
* Track **security bulletins & patches** for all acquired software.  
* Verify regulatory compliance (**GDPR, HIPAA, PCI-DSS, etc.**) in vendor contracts.  
* Implement **continuous vulnerability scanning** of deployed COTS / OSS.  

#### ****Testing Requirements****
1. **Internal testing** – Static & dynamic analysis, fuzzing, integration tests.  
2. **Vendor-provided results** – Review penetration & code-quality reports.  
3. **Independent third-party testing** – Objective validation of security claims.  

#### ****Action Checklist ✅****
* Maintain inventory of **all third-party software & versions**.  
* Define **SLA / SLR clauses** for security updates & incident reporting.  
* Require vendors to support **security audit rights** in contracts.  
* Ensure secure management of **API keys & secrets** used with SaaS services.  
* Automate patch deployment pipelines to reduce **mean-time-to-remediate (MTTR)**.  

## Establishing Databases and Data Warehousing  

### Database Management System Architecture  
Modern enterprises rely heavily on database platforms; safeguarding them 🛡️ is critical for **confidentiality, integrity, and availability (CIA)**.  

##### Hierarchical & Distributed DBMS  
* **Hierarchical DBMS** – One-to-many *tree* (parent ➜ child) structure.  
  * Examples: corporate org-chart, DNS namespace.  
  * Fast retrieval along defined paths but poor ad-hoc query flexibility.  
* **Distributed DBMS** – Data stored on multiple networked nodes yet appears as a single logical DB.  
  * Many-to-many relationships; supports fault-tolerance & load-balancing.  
  * Requires synchronization, replication, and strong network security.  

##### Relational DBMS (RDBMS)  
* Stores information in **two-dimensional tables (relations)** of rows (**tuples**) & columns (**attributes**).  
* Enforces **one-to-one** data mapping and supports **SQL** for interaction.  
* Key Terms 🔑  
  | Key Type | Purpose | Example |  
  |----------|---------|---------|  
  | Candidate | Any field(s) uniquely identifying a row | Company ID, Telephone |  
  | Primary | Chosen candidate used for uniqueness | Company ID |  
  | Alternate | Remaining candidate keys not selected | Telephone |  
  | Foreign | Refers to PK in another table; ensures **referential integrity** | Sales Rep ID |  
* **Cardinality** – # of rows. **Degree** – # of columns.  
* **SQL Components**:  
  * **DDL** – CREATE / ALTER schemas.  
  * **DML** – SELECT / INSERT / UPDATE / DELETE data.  
  * Fine-grained authorization—limit by table, column, row, view.  

##### Object-Relational & Object-Oriented DBMS  
* Extend relational model with **objects, classes, inheritance**.  
* Better for multimedia, CAD, complex data & code reuse.  

#### Database Transactions 🔄  
| ACID Property | Description | Security Benefit |  
|---------------|-------------|------------------|  
| Atomicity | “All-or-nothing”; rollback on failure | Prevents partial updates ↩️ |  
| Consistency | Transaction leaves DB in valid state | Preserves integrity ✔️ |  
| Isolation | Concurrent transactions don’t interfere | Thwarts race conditions |  
| Durability | Committed data survives crashes | Aids availability |  

*Typical flow:* `BEGIN TRAN; … COMMIT;` or `ROLLBACK;`  

#### Security for Multilevel Databases  
* **Polyinstantiation** – Multiple rows with same PK but different secrecy labels; stops inference across clearance levels.  
* **Views** – Virtual tables exposing only permitted columns/rows 🧐 (least privilege).  
* **Concurrency Controls** – Locks & journaling prevent **lost-update** and **dirty-read** weaknesses.  
* **Aggregation** – Combining low-level data to infer sensitive info; mitigate via query restriction & need-to-know.  
* **Inference** – Deduction of protected data from allowed queries; counter with data masking, partitioning, noise.  

#### Database Connectivity & Middleware  
* **Open Database Connectivity (ODBC)** – Standard API that allows apps to talk to many DBMS engines; secure via strong authentication & encrypted channels (e.g., TLS).  
* **JDBC / OLE DB / ADO.NET** similar concepts in other ecosystems.  

#### Database Normalization ⚙️  
| Normal Form | Goal | Key Requirement |  
|-------------|------|-----------------|  
| 1NF | Eliminate duplicate columns; atomic values | Unique rows/columns |  
| 2NF | Remove partial dependency on PK | All non-PK attrs depend on whole PK |  
| 3NF | Remove transitive dependency | Non-PK attrs depend **only** on PK |  
*Normalization reduces redundancy & update anomalies, enhancing integrity and efficiency.*  

#### Machine Learning & Big-Data Warehousing  
* **Data Warehouses** – Central repositories that aggregate cleansed data from multiple sources for analytics.  
* **Data Lakes** – Store raw, often unstructured, data for ML processing.  
* Security Focus:  
  * Encryption at rest & in transit.  
  * Access segmentation between analytic jobs.  
  * Audit logging for compliance (e.g., GDPR, HIPAA).  

#### Threats & Countermeasures Overview  
| Threat 🚨 | Description | Control 🛡️ |  
|-----------|-------------|-------------|  
| SQL Injection | Manipulate queries via unsanitized input | Parametrized statements, input validation |  
| Excessive Privileges | Broad DB roles granted to users/apps | RBAC, least privilege, periodic reviews |  
| Backup Exposure | Unencrypted dumps copied off-site | Encrypt backups, strong key mgmt |  
| Metadata Leakage | Optional schema info aids attackers | Restrict system tables, strip error msgs |  
| DoS on DB | Lock tables, exhaust connections | Connection throttling, replication, HA |  

#### Exam Tips ✏️  
* Remember **polyinstantiation** vs. **views** for multilevel security.  
* **ACID** is core for transaction integrity—expect direct questions.  
* Know **SQL authorization granularity** (table ➜ row ➜ column).  
* **Foreign keys enforce referential integrity**; primary keys ensure uniqueness.  
* **Aggregation/inference** are distinct but related confidentiality risks.  

### Database Transactions  

#### Transaction Fundamentals  
Relational DBMSs group SQL statements into **transactions** to protect data integrity.  
*Example* 📑  
    BEGIN TRAN
    UPDATE accounts SET balance = balance + 250 WHERE account_number = 1001;
    UPDATE accounts SET balance = balance - 250 WHERE account_number = 2002;
    COMMIT;   -- implicit if no error  
If any statement fails, **ROLLBACK** reverts the DB to its prior state.  

#### Commit vs. Rollback  
| Command | Purpose | Effect |  
|---------|---------|--------|  
| `COMMIT` | Ends & saves a successful transaction | Changes become permanent |  
| `ROLLBACK` | Aborts/undoes a transaction | DB returns to pre-transaction state |  
| Implicit Commit | Automatic on success | Same as explicit `COMMIT` |  
| Implicit Rollback | Automatic on crash/error | Same as explicit `ROLLBACK` |  

#### ACID Model 🚦  
| Property | Definition | CISSP Security Impact |  
|----------|------------|-----------------------|  
| **Atomicity** | “All-or-nothing” – partial writes forbidden | Prevents partial updates, preserves integrity |  
| **Consistency** | Begins & ends in rule-compliant state | No constraint violations escape a txn |  
| **Isolation** | Concurrent txns don’t see intermediates | Stops race conditions / dirty reads |  
| **Durability** | Committed data survives failures | Logs, journaling, RAID/backups ensure survival |  

##### Concurrency Problems & Controls  
| Issue | Example | Mitigation |  
|-------|---------|------------|  
| **Lost Update** | Two commits overwrite each other | Row/column locks |  
| **Dirty Read** | Txn reads uncommitted data | Isolation levels (e.g., SERIALIZABLE) |  
| **Non-repeatable Read** | Same query returns different results within txn | Snapshot isolation, MVCC |  
| **Phantom Read** | New rows appear/disappear | Range locks, SERIALIZABLE isolation |  

#### Security Mechanisms for Transactions  
* **Transaction Logs / Write-Ahead Logging (WAL)** – foundation for durability & forensic auditing.  
* **Granular Access Control** – limit who can `BEGIN TRAN` on sensitive tables.  
* **Input Validation** – 🚫 SQL injection can subvert transactional logic. Use parameterized queries.  
* **Backup & Recovery Strategy** – hot backups, point-in-time recovery safeguard committed data.  

#### Exam Tips ✏️  
* Recall **A-C-I-D** order & definitions.  
* System failure before commit ⇒ automatic **ROLLBACK**.  
* Isolation covers *dirty, non-repeatable, phantom* reads—know each term.  
* Transaction logs serve both **durability** *and* **audit** roles.  

### Security for Multilevel Databases  

#### Overview  
Modern DBMSs often **store records at multiple classification levels** (e.g., Public, Confidential, Secret). Multilevel security (MLS) enforces mandatory access controls so that users 🧑‍💼 only see data matching their clearance **and** need-to-know. Key concerns:  
* **Database contamination** – mixing data of different levels in the same table/view  
* **Unauthorized disclosure** – inference & aggregation attacks  
* **Integrity & Availability** – concurrency control  
  
#### Database Contamination & Trusted Front End  
* **Contamination** 🦠 occurs when high- and low-level data coexist in ways that weaken controls  
* **Trusted Front End** – security “gateway” that:  
  * Enforces labels before queries reach a legacy or insecure DBMS  
  * Sanitizes results to remove restricted rows/columns or apply polyinstantiation  
  * Logs/audits access attempts for non-repudiation  

#### Restricting Access with Views  
Views = stored SQL queries that masquerade as tables. Benefits:  
* Present **least-privilege slices** 🍰 of data (row/column/cell level)  
* Join or aggregate data from multiple tables without storing duplicate info  
* Hide sensitive columns or classified records from low-level users  
| Feature | Tables | Views |  
|---------|--------|-------|  
| Physical Storage | Yes | No (stored query) |  
| Follows Normalization | Must | Can violate |  
| Performance | Fast | May require on-the-fly calc |  
| Security Use | Limited | Fine-grained access control |  

#### Concurrency Control 🔄  
Ensures integrity when **multiple users edit simultaneously**. Core tool: *locking*.  
* **Lost Update** – parallel changes overwrite each other  
* **Dirty Read** – txn reads uncommitted data  
* Locks (row, page, table) prevent overlap; released at commit/rollback  
* Concurrency + auditing ⇒ *preventive & detective* control  

#### Aggregation ⚖️  
Attackers combine multiple low-level facts to reveal higher-level info (e.g., counting troop numbers). Countermeasures:  
* Restrict `COUNT`, `SUM`, `AVG`, etc., via RBAC  
* Apply **need-to-know & least privilege**  
* Noise/perturbation – introduce statistical fuzzing to blur outputs  

#### Inference 🕵️‍♂️  
Logical deduction by correlating seemingly innocuous data points. Example: salary total before/after single hire ⇒ individual salary. Controls:  
* Limit historical queries / date ranges  
* **Blurring**: round values, return ranges rather than exact numbers  
* **Database partitioning** – split data into separate DBs by level  
* Polyinstantiation (see below)  

#### Other Security Mechanisms  
| Mechanism | Purpose | Key Point for CISSP |  
|-----------|---------|---------------------|  
| **Semantic Integrity** | Enforce data rules/constraints 📏 | Stops invalid or out-of-range entries |  
| **Timestamp Ordering** | Chronological replication in distributed DBs | Maintains consistency |  
| **Content-Dependent Control** | Checks data payload before access | High overhead, fine granularity |  
| **Context-Dependent Control** | Considers overall situation (session, query mix) | Identifies malicious patterns |  
| **Cell Suppression** | Hide individual fields/cells | Prevents leakage |  
| **Database Partitioning** | Separate DBs by sensitivity | Mitigates inference/aggregation |  
| **Noise & Perturbation** | Insert fake data ✨ | Deceive attackers, must not harm ops |  
| **Polyinstantiation** | Multiple records with same PK but different classification | Supports MLS, thwarts inference |  

##### Polyinstantiation Example  
| Ship | Classification | Position |  
|------|---------------|----------|  
| USS UpToNoGood | **Top Secret** | 18°N 77°W |  
| USS UpToNoGood | **Secret** | Routine Patrol Area |  
Low-clearance users see only the lower-level row; high-clearance users see both.  

#### Exam Tips ✏️  
* Contamination = mixed-level data → use trusted front end or DB partitioning.  
* **Views = least-privilege windows** into tables.  
* Concurrency issues: *lost update* vs. *dirty read*—locks & ACID isolation resolve.  
* Aggregation ≠ inference: aggregation uses DB math, inference uses human deduction.  
* Remember **polyinstantiation** definition & MLS role.

### Open Database Connectivity
* **Purpose**: Acts as a middleware 🔄 between applications and diverse backend DBMSs, enabling **DB-vendor independence**.  
* **How It Works**  
  1. Application issues generic SQL.  
  2. ODBC driver manager receives request.  
  3. Appropriate DB-specific driver translates SQL & communicates with DB.  
* **CISSP Takeaways**  
  * Simplifies coding but adds an extra layer—**secure configuration & patching** of drivers is essential.  
  * Restrict ODBC drivers to **least privilege**; disable unused drivers to reduce attack surface.  
  * Monitor ODBC logs for anomaly detection.  

| ODBC Security Concern | Mitigation |  
|-----------------------|------------|  
| Rogue/unused drivers | Remove/disable 📛 |  
| Injection via driver  | Harden input, use parameterized queries |  
| Driver spoofing       | Sign & verify driver binaries, patch promptly |  

### NoSQL 
Modern workloads (big data, flexible schemas, real-time analytics) often **outgrow RDBMS limits**. *NoSQL* = “Not Only SQL”—databases using non-tabular data models.  

##### Common NoSQL Families  
| Type | Data Model | Strengths | Example Use Cases |  
|------|------------|-----------|-------------------|  
| **Key-Value Store** | `{key : value}` | Ultra-fast lookups, massive scale | Session data, caching |  
| **Document Store** | Semi-structured docs (JSON, XML) | Flexible schema, hierarchical data | Content management, IoT |  
| **Graph DB** | Nodes & edges | Complex relationships, traversals | Social networks 🌐, fraud detection |  
| **Column Family** | Sparse columnar | High write throughput, analytics | Log aggregation, time series |  

##### Security Implications  
* **Access Control Models vary** – may lack mature role-based controls of RDBMS; integrate with external IAM.  
* **Data at Rest/In Transit** – ensure encryption options enabled; some NoSQL products disable TLS by default.  
* **Replication & Sharding** – secure inter-node channels, authenticate cluster members to prevent rogue node injection.  
* **Input Validation** still vital – many NoSQL engines are subject to injection attacks (e.g., MongoDB query injection).  

##### CISSP Exam Tips ✏️  
* ODBC = interoperability layer—keep drivers patched & restrict usage.  
* NoSQL **does not imply insecurity**, but security controls differ—know key types & matching controls.  
* Remember key security tasks: enable authentication 🔐, encrypt data, least-privilege user roles, secure clusters.

## Storage Threats  

### Overview  
* DBMS controls protect data only via authorized “front-door” queries.  
* **Storage layers**—memory, disks, SSDs, cloud buckets—remain vulnerable if not separately secured.  
* CISSP focus ➡️ understand risks of ➡️ **illegitimate access** & **covert storage channels**.  

### Illegitimate Access to Storage Resources  
* **Weak File-System Permissions** – Unprotected directories/files allow attackers to browse 🔍 and extract sensitive data.  
* **Bypassing OS Controls** – Attackers boot alternate OS or remove drives to read raw blocks; defense = **full-disk / file-system encryption**.  
* **Multilevel Security (MLS) Concerns** – Shared memory/disk buffers must enforce **label dominance**; high-level data must not bleed to lower levels.  
* **Cloud Storage Misconfiguration** ☁️  
  * Public-read buckets (e.g., mis-set S3 ACLs) expose data to the internet.  
  * Countermeasures:  
    1. Default **deny-all** policies.  
    2. Continuous configuration monitoring & alerting.  
    3. Encrypt objects server-side / client-side.  

| Risk | Impact | Mitigation |  
|------|--------|------------|  
| Weak ACLs | Data disclosure | Least-privilege, periodic audits 📝 |  
| Raw-disk access | Bypass DB/OS, theft | Full-disk encryption, UEFI/Secure Boot |  
| Cross-domain reads | MLS violation | Mandatory Access Control (MAC), data labeling |  
| Cloud bucket exposure | Public leaks 🌐 | Tight IAM, bucket policies, encryption |  

### Covert Storage Channels 🕵️‍♂️  
* **Definition**: Indirectly transferring information between security levels by manipulating shared storage.  
* **Simple Example**: High process writes secret to a world-readable temp file; low process reads file.  
* **Advanced Techniques**:  
  * Modifying file size / timestamp to encode bits.  
  * Altering free disk space or memory allocation patterns.  
* **Countermeasures**  
  * Strict MAC—prevent lower classification reads on higher-level objects.  
  * Partition storage per security level; use **trusted mediators**.  
  * Employ auditing & covert-channel analysis (see Ch 8) to estimate bandwidth and apply noise/randomization.  

### CISSP Exam Tips ✏️  
* Remember: encrypting data **in storage and in transit** supplements, not replaces, DBMS permissions.  
* Cloud storage threats focus on **misconfiguration**, not vendor hypervisor hacks.  
* Covert channels ➡️ two types: **storage vs. timing**; here we cover storage. Blocking requires *eliminating shared resources* or *strict mediation*.

## Understanding Knowledge-Based Systems  
Since the advent of computing, engineers and scientists have pursued systems that relieve humans of tedious or time-consuming tasks. Beyond raw calculation, research also targets **artificial intelligence (AI)** capable of human-like reasoning.  
This section surveys three AI approaches—**expert systems, machine learning, and neural networks**—and notes their security applications.

### Expert Systems  

* **Goal** – Capture expert knowledge and apply it consistently to routine decisions.  
* **Core Components**  
  1. **Knowledge Base** – Collection of *if/then* rules representing expert insight.  
     *Example hurricane rules (illustrative only):*  
       * If hurricane ≥ Category 4 → floodwaters ≈ 20 ft.  
       * If winds > 120 mph → wood-frame structures destroyed.  
  2. **Inference Engine** – Applies logical / fuzzy reasoning to knowledge-base rules in light of user-supplied facts to reach conclusions.  
* **Strength** – Provides emotion-free, rapid, repeatable decisions (e.g., credit scoring, emergency response).  
* **Limitation** – Only as good as rule quality and inference algorithms.

### Machine Learning  
* **Definition** – Algorithms derive models directly from data rather than explicit rules.  
* **Categories**  
  * **Supervised Learning** – Trains on labeled data (input + correct output).  
    *Ex.* Build model of malicious logins using historical data tagged “malicious” vs. “normal.”  
  * **Unsupervised Learning** – Finds structure in unlabeled data (clustering, association).  
    *Ex.* Group similar logins; analyst inspects clusters for anomalies.  

### Neural Networks  
* **Concept** – Chains of weighted computational units imitate biological neurons; subset of machine learning (*deep learning*).  
* **Benefits** – Linearity, adaptable input-output mapping, ability to “learn” via training.  
* **Training** – Adjusts connection weights using the **Delta rule** to minimize error between predicted and known outputs.  
* **Applications** – Voice / face recognition, weather prediction, cognitive modeling.  

#### Security Applications  
* Rapid, consistent anomaly detection in vast log/audit datasets.  
* Reduction of human error in repetitive security tasks (alert triage, threat classification).  
* Potential foundations for adaptive, self-learning defensive systems.  

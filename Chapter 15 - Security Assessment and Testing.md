# Chapter 15: Security Assessment and Testing

- [Building a Security Assessment and Testing Program]()
  - [Security Testing]()
  - [Security Assessments]()
  - [Security Audits]()
- [Performing Vulnerability Assessments]()
  - [Describing Vulnerabilities]()
  - [Vulnerability Scans]()
  - [Penetration Testing]()
  - [Compliance Checks]()
- [Testing Your Software]()
  - [Code Review and Testing]()
  - [Interface Testing]()
  - [Misuse Case Testing]()
  - [Test Coverage Analysis]()
  - [Website Monitoring]()
- [Training and Exercises]()
- [Implementing Security Management Processes and Collecting Security Process Data]()
  - [Log Reviews]()
  - [Account Management]()
  - [Disaster Recovery and Business Continuity]()
  - [Training and Awareness]()
  - [Key Performance and Risk Indicators]()
- [Summary]()

## Building a Security Assessment & Testing Program  
Establishes a structured cycle of **tests, assessments, and audits** that confirm controls exist, work as intended, and protect assets across on-prem, cloud, and hybrid environments.

### Security Testing  
Tool-driven or manual **control checks** (e.g., vulnerability scans, pen-tests).  
Scheduling is risk-based—considering resource availability, system criticality, data sensitivity, probability of failure/attack, change rate, business impact, and test difficulty.  
Results are **reviewed, prioritized, and acted on**; alerts or tickets are raised for significant findings.

### Security Assessments  
Holistic, **human-led risk reviews** that combine testing results with threat context and asset value.  
Deliverable is a **management report** written in plain language with specific remediation advice.  
May be performed by internal staff or third-party specialists.

#### NIST SP 800-53A  
U.S. best-practice guide for assessing security & privacy controls.  
Looks at four “assessment objects”:  
* **Specifications** (policies, designs)  
* **Mechanisms** (technical controls)  
* **Activities** (operational tasks)  
* **Individuals** (people operating controls)  

Assessors **examine, interview, and test** to judge control effectiveness.

### Security Audits  
Independent evaluations aimed at proving control effectiveness to outsiders (board, regulators, customers).

| Audit Type | Who Performs | Primary Audience |
|------------|--------------|------------------|
| **Internal** | In-house audit team with separate reporting line | Leadership / board |
| **External** | Independent audit firm (often “Big Four”) | Investors / regulators |
| **Third-Party** | Hired by an external stakeholder (e.g., regulator, customer) | The hiring organization |

#### SOC Reports (SSAE 18 / ISAE 3402)  
Standardized attestation that lets service providers undergo **one audit** and share the report widely.

* **SOC 1** – Controls impacting financial reporting  
* **SOC 2** – Controls protecting security, availability, processing integrity, confidentiality, privacy (results under NDA)  
* **SOC 3** – Same scope as SOC 2 but **publicly shareable**

Report levels:  
* **Type I** – Snapshot: design suitability only  
* **Type II** – Operating effectiveness tested over ≥ 6 months (more credible)

#### Case Study – GAO FAA Audit  
A 2015 **Government Accountability Office** review found serious cyber weaknesses in U.S. air-traffic-control systems and issued 17 remediation recommendations—illustrating the impact of third-party audits on critical infrastructure.

#### Auditing Standards  
* **COBIT** – ISACA framework defining control objectives for IT governance and assurance.  
* **ISO 27001 / 27002** – International standards for building and measuring an Information Security Management System (ISMS); organizations may become ISO 27001-certified.

---



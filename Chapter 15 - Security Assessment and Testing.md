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

```mermaid
mindmap
  root((Chapter 15<br>Security Assessment & Testing))
    Program
      Scope:::leaf(On-prem • Cloud • Hybrid)
    Tests
      "Purpose:\nVerify control works"
      Methods
        "Automated\nvuln scans"
        "Tool-assisted\npen tests"
        "Manual\nexploits"
      "Scheduling Factors"
        Resources
        Criticality
        Sensitivity
        "Tech failure\nlikelihood"
        "Misconfig\nprobability"
        "Attack/threat\nrisk"
        "Rate of\nchange"
        "Env.\nchanges"
        "Test effort &\ntime"
        "Business\nimpact"
      Results
        "Manual review"
        "Automated\nalert/ ticket"
    Assessments
      "Comprehensive\nrisk review"
      "Outputs:\nMgmt report + recs"
      Teams
        Internal
        External
      "NIST SP 800-53A"
        Specifications
        Mechanisms
        Activities
        Individuals
    Audits
      "Independent\nassurance"
      Types
        "Internal\nAudit"
        "External\nAudit"
        "Third-Party\nAudit"
      "SOC / SSAE-18\n(ISAE 3402)"
        "SOC 1\n(Financial)"
        "SOC 2\n(Sec/Privacy)"
        "SOC 3\n(Public)"
        "Report Types"
          "Type I\n(Design, point-in-time)"
          "Type II\n(Effectiveness, ≥6 mo)"
      Frameworks
        COBIT
        "ISO 27001"
        "ISO 27002"
      Example
        "2015 GAO audit\nFAA ATC flaws"
    KeyTakeaways
      "Tests vs\nAssess vs\nAudit"
      "Risk-prioritized\nroutine testing"
      "Independence in\naudits"
      "Cover all\nenvironments"
```

> **Goal of the chapter:** Understand how to **plan, execute, and evaluate** tests, assessments, and audits that prove security controls are *present, operating correctly, and effective* across on-prem, cloud, and hybrid environments.

## Building a Security Assessment & Testing Program
| What | Why |
|------|-----|
|**Security Tests**|Verify **control operation** (working as intended).|
|**Security Assessments**|Broader **risk-focused reviews**; identify & remediate weaknesses.|
|**Security Audits**|**Independent attestation** that controls meet a defined standard; results shared with 3rd-parties.|

> ✅ **CISSP-Key:** A *test* checks a control; an *assessment* weighs risk & gives recs; an *audit* proves compliance **independently**.

### Security Testing
#### Definition  
Automated scans, tool-assisted pen tests, or manual exploits run on a **scheduled, risk-prioritized** basis.

#### Scheduling / Prioritization Factors  
- ❑ Testing resources available  
- ❑ **Criticality** of protected systems  
- ❑ **Sensitivity** of data involved  
- ❑ Tech **failure** likelihood  
- ❑ **Misconfiguration** probability  
- ❑ Threat / **attack** risk  
- ❑ Rate **of change** of control  
- ❑ Environmental changes  
- ❑ Effort & **business impact** of test  

#### Good Practice  
1. Design a **comprehensive plan** (no haphazard “scan-everything” approach).  
2. Blend **frequent automated** scans (low impact) with **periodic manual** testing (higher assurance).  
3. **Review results**:  
   * Manual analyst validation *or*  
   * Automated log + alert/ticket on findings.  

### Security Assessments
#### Definition  
A **trained security professional** performs a holistic risk assessment, factoring **threats, vulnerabilities, asset value, and future risks**.  
**Deliverable:** *Management report* (plain language) + **remediation recommendations**.

#### Execution  
- May be **internal** or **outsourced**.  
- Uses testing tools **plus** reasoning & expert judgment (beyond raw scan output).

#### NIST SP 800-53A “Assessing Security & Privacy Controls”  
| Assessment **Objects** | Meaning |
|-|-|
|**Specifications**|Docs: policies, procedures, requirements, designs.|
|**Mechanisms**|Security controls (hw / sw / fw).|
|**Activities**|Human actions (backups, log reviews).|
|**Individuals**|People who implement the above.|

*Assessors **examine, interview, and test** these objects to rate control effectiveness.*

### Security Audits
**Purpose:** Provide an **impartial, unbiased opinion** on control effectiveness against a standard.  
*Must be performed by auditors **independent** of those who design/operate the controls.*

#### Audit Types  
| Type | Who controls scope? | Typical Audience |
|-|-|-|
|**Internal**|Organization’s own **independent audit dept** | Management / Board |
|**External**|Outside audit firm hired by org (e.g., **Big 4**) | Shareholders, regulators |
|**Third-Party**|Initiated & scoped by **another entity** (client, regulator) | Requesting entity |

> **Exam Tip:** *Control of the engagement* distinguishes internal, external, and third-party audits.

#### SOC / SSAE-18 / ISAE 3402 Audits  
| Engagement | Focus |
|-|-|
|**SOC 1**|Controls that affect **financial reporting**.|
|**SOC 2**|Controls over **security, availability, confidentiality, processing integrity, privacy** (results = confidential).|
|**SOC 3**|Same domains as SOC 2, but **public report**.|

**Report Types**  
- **Type I:** Design & description of controls at a **point-in-time**.  
- **Type II:** Design **and operating effectiveness** over **≥ 6 months** (more trusted on the exam).

#### Real-World Example  
*2015 GAO audit* → found significant weaknesses in **FAA Air Traffic Control** systems (boundary, authn, encryption, logging).

#### Auditing Standards & Frameworks
| Standard | Use in CISSP context |
|-|-|
|**COBIT (ISACA)**|Control objectives for IT & assurance framework.|
|**ISO 27001**|Specifies **ISMS** requirements (can certify).|
|**ISO 27002**|Code of practice — detailed **control catalog**.|

*(Know that audits/assessments compare org controls to a chosen **standard**.)*

#### Key Takeaways for the Exam
1. **Test ≠ Assessment ≠ Audit** – know definitions & goals.  
2. **Risk-prioritized schedule** drives testing frequency.  
3. Assessment objects per **NIST 800-53A:** specifications, mechanisms, activities, individuals.  
4. Audit independence: internal vs external vs third-party; **SOC reports (Type I vs II)**.  
5. Common frameworks (COBIT, ISO 27001/27002) provide **control objectives** for audits.

---



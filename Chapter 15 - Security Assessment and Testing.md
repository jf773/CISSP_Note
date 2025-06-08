# Chapter 15: Security Assessment and Testing

- [Building a Security Assessment and Testing Program](#building-a-security-assessment-and-testing-program)
  - [Security Testing](#security-testing)
  - [Security Assessments](#security-assessments)
  - [Security Audits](#security-audits)
- [Performing Vulnerability Assessments](#performing-vulnerability-assessments)
  - [Describing Vulnerabilities](#describing-vulnerabilities)
  - [Vulnerability Scans](#vulnerability-scans)
  - [Penetration Testing](#penetration-testing)
  - [Compliance Checks](#compliance-checks)
- [Testing Your Software](#testing-your-software)
  - [Code Review and Testing](#code-review-and-testing)
  - [Interface Testing](#interface-testing)
  - [Misuse Case Testing](#misuse-case-testing)
  - [Test Coverage Analysis](#test-coverage-analysis)
  - [Website Monitoring](#website-monitoring)
- [Training and Exercises](#training-and-exercises)
- [Implementing Security Management Processes and Collecting Security Process Data](#implementing-security-management-processes-and-collecting-security-process-data)
  - [Log Reviews](#log-reviews)
  - [Account Management](#account-management)
  - [Disaster Recovery and Business Continuity](#disaster-recovery-and-business-continuity)
  - [Training and Awareness](#training-and-awareness)
  - [Key Performance and Risk Indicators](#key-performance-and-risk-indicators)
- [Summary](#summary)


```mermaid
mindmap
  root((Chapter 15 – Security Assessment & Testing))

    %% 1. Build the programme
    Building a Security Assessment & Testing Program
      Security Tests
        Automated Scans
        Tool-Assisted Pen Tests
        Manual Tests
      Security Assessments
        Risk-Focused Review
        NIST SP 800-53A (Objects)
          Specifications
          Mechanisms
          Activities
          Individuals
      Security Audits
        Internal Audit
        External Audit
        Third-Party Audit
          SSAE-18 / ISAE 3402
            SOC 1 (Financial Reporting)
            SOC 2 (Security & Privacy - NDA)
            SOC 3 (Security & Privacy - Public)

    %% 2. Vulnerability assessment workflow
    Performing Vulnerability Assessments
      Describing Vulnerabilities
      Vulnerability Scans
      Penetration Testing
      Compliance Checks

    %% 3. Software testing techniques
    Testing Your Software
      Code Review & Testing
      Interface Testing
      Misuse Case Testing
      Test Coverage Analysis
      Website Monitoring

    %% 4. Training / Exercises
    Training and Exercises

    %% 5. Security-management data collection
    Implementing Security Management Processes & Collecting Data
      Log Reviews
      Account Management
      DR & Business Continuity
      Training & Awareness
      Key Performance & Risk Indicators

    %% 6. Chapter wrap-up
    Summary
```

> **Goal of the chapter:** Understand how to **plan, execute, and evaluate** tests, assessments, and audits that prove security controls are *present, operating correctly, and effective* across on-prem, cloud, and hybrid environments.

## Building a Security Assessment and Testing Program
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
- ❑ Availability of security testing resources
- ❑ Criticality of the systems and applications protected by the tested controls
- ❑ Sensitivity of information contained on tested systems and applications
- ❑ Likelihood of a technical failure of the mechanism implementing the control
- ❑ Likelihood of a misconfiguration of the control that would jeopardize security
- ❑ Risk that the system will come under attack
- ❑ Rate of change of the control configuration
- ❑ Other changes in the technical environment that may affect the control performance
- ❑ Difficulty and time required to perform a control test
- ❑ Impact of the test on normal business operations

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



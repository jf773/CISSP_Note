# Chapter 4 — Laws, Regulations & Compliance  

- [Categories of Laws](#categories-of-laws)
  - [Criminal Law](#criminal-law)
  - [Civil Law](#civil-law)
  - [Administrative Law](#administrative-law)
- [Laws](#laws)
  - [Computer Crime](#computer-crime)
  - [Intellectual Property (IP)](#intellectual-property-ip)
  - [Software Licensing](#software-licensing)
  - [Import/Export](#importexport)
  - [Privacy](#privacy)
- [State Privacy Laws](#state-privacy-laws)
- [Compliance](#compliance)
- [Contracting and Procurement](#contracting-and-procurement)
- [Summary](#summary)


```mermaid
mindmap
  root((Chapter 4 – Laws, Regulations & Compliance))

    Categories of Laws
      Criminal Law
        State prosecution
        Fines and imprisonment
      Civil / Tort Law
        Party vs party
        Damages and injunctions
      Administrative / Regulatory Law
        Agency rules
        Monetary penalties

    Major Laws
      Computer Crime
        CFAA
        DMCA
        CAN-SPAM
      Intellectual Property
        Copyright
        Patent
        Trademark
        Trade secret
      Software Licensing
        EULA
        FOSS licenses
        SaaS terms
      Import / Export Controls
        ITAR
        EAR
        Crypto export rules
      Privacy (Global)
        GDPR
        HIPAA
        GLBA
        CCPA / CPRA

    State Privacy Laws
      NY SHIELD Act
      VA VCDPA
      CO CPA

    Compliance Frameworks
      PCI-DSS
      SOX
      ISO 27001
      SOC 1 &amp; SOC 2
      FedRAMP

    Contracting & Procurement
      Service Level Agreements
      Master Service Agreement
      Indemnity & liability caps
      Right to audit
      Vendor due diligence

    Exam Flags
      GDPR penalties 4 % or €20 M
      Copyright arises automatically
      AES export governed by EAR
      Security clauses in contracts
```

## Categories of Laws  
**Core idea:**  Different legal branches govern how infractions are prosecuted and penalized. Know which applies to a given security scenario.
U.S. information-security professionals routinely encounter **three categories of law**.  
Understanding the purpose, scope, enforcement, and CISSP implications of each helps determine when to call legal counsel and how to design compliant security programs.

| Law Category | What It Covers | Who Enforces It | Typical Penalties | CISSP Angle |
|--------------|---------------|-----------------|-------------------|-------------|
| **Criminal Law** | Acts viewed as offenses against society (e.g. hacking, fraud, assault, arson) | Prosecutors, police, FBI/Secret Service, DoJ | Fines, imprisonment, community service, loss of civil liberties | Know key federal cyber-crime statutes (CFAA, ECPA, ITADA, etc.) and incident-response evidence handling. |
| **Civil Law** | Disputes between private parties (contracts, employment, real-estate, negligence) | Plaintiff’s attorneys; adjudicated by civil courts | Monetary damages, injunctions, specific performance | Contract language, SLAs, privacy and negligence exposure; common source of **liability** for data breaches. |
| **Administrative Law** | Regulations issued by executive-branch agencies to operationalize statutes (e.g. FCC, FTC, DHS, SEC rules) | Regulator itself (audits, fines); reviewed by courts | Fines, revocation of licenses, cease-and-desist orders | Compliance frameworks (HIPAA, GLBA, SOX, FISMA, FedRAMP) stem from administrative rules; non-compliance can trigger separate civil/criminal actions. |

### Criminal Law

* **Purpose** – Protect society at large, deter harmful acts, and punish offenders.  
* **Source** – Federal & state legislatures; must align with the U.S. Constitution.  
* **Process** – Government (prosecution) vs. defendant; burden of proof *beyond a reasonable doubt*.  
* **Cyber-Security Focus**  
  * **Computer Fraud and Abuse Act (CFAA)** – Primary federal anti-hacking statute.  
  * **ECPA & Wiretap Act** – Unauthorized interception of electronic communications.  
  * **Identity Theft & Assumption Deterrence Act (ITADA)** – Criminalizes identity theft.  
* **Exam Tip** – Be able to cite when criminal authorities must be involved and understand chain-of-custody requirements for digital evidence.

---

### Civil Law

* **Purpose** – Resolve non-criminal disputes and provide restitution to injured parties.  
* **Source** – Same legislative process as criminal law; codified in the **United States Code (USC)** or state statutes.  
* **Process** – Plaintiff vs. defendant; burden of proof is *preponderance of evidence* (lower threshold).  
* **Cyber-Security Focus**  
  * **Tort liability** – Negligence in safeguarding PII may result in class-action lawsuits.  
  * **Contract enforcement** – Breach of NDA or SLA due to security failure.  
* **Exam Tip** – Understand organizational exposure to civil suits after a breach and the role of insurance, due care, and due diligence.

---

### Administrative Law

* **Purpose** – Enable executive agencies to implement and enforce detailed regulations that support statutes.  
* **Source** – Published in the **Code of Federal Regulations (CFR)**; must not conflict with higher laws.  
* **Process** – Agency rule-making (notice-and-comment), compliance audits, fines; subject to judicial review.  
* **Cyber-Security Focus**  
  * **NIST standards via FISMA/FISMA-2014** (e.g. SP 800-53)  
  * **HIPAA Security Rule** (HHS), **GLBA Safeguards Rule** (FTC), **SOX IT controls** (SEC/PCAOB)  
  * **FTC Act §5** – “Unfair or deceptive” practices for poor security.

* **Exam Tip** – Map administrative requirements to controls; ensure policies and procedures satisfy agency mandates to avoid fines and injunctions.

---

> **Remember for CISSP:**  
> *Criminal = society vs. individual, Civil = individual vs. individual, Administrative = agency rules.* Always verify which category applies before acting, and engage qualified legal counsel for gray areas.

---

## Laws  

| Domain | Law / Regulation (+ Legal Type) | Brief Description | Oversight / Enforcement Agency (Primary Jurisdiction) |
|--------|----------------------------------|-------------------|-------------------------------------------------------|
| **Privacy** | **GDPR** — General Data Protection Regulation (EU) *(Administrative / Civil)* | Comprehensive EU-wide data-protection law with extraterritorial reach; 72-hr breach notice; fines up to 4 % global turnover. | European Data Protection Board (EDPB) / Supervisory Authorities (each member state) |
|  | **Privacy Act 1974** (USA) *(Civil / Administrative)* | Limits what U.S. federal agencies may collect, use, and disclose; gives individuals access / amendment rights. | Office of Management and Budget (OMB) + individual federal agencies |
|  | **PIPEDA** — Personal Information Protection and Electronic Documents Act (Canada) *(Civil / Administrative)* | Governs commercial-sector personal data; grants access, correction, and consent rights; allows “substantially similar” provincial laws. | Office of the Privacy Commissioner of Canada (OPC) |
|  | **POPIA** — Protection of Personal Information Act 2020 (South Africa) *(Civil / Administrative)* | Eight GDPR-like processing conditions; regulates consent, purpose, special-category data; heavy fines/prison for violations. | Information Regulator (South Africa) |
|  | **PIPL** — Personal Information Protection Law 2021 (China) *(Civil / Administrative)* | China’s first omnibus privacy law: explicit consent, data-minimization, security measures, outbound-transfer restrictions, steep fines. | Cyberspace Administration of China (CAC) |
|  | **CCPA / CPRA** — California Consumer Privacy / Privacy Rights Acts (USA-CA) *(Civil / Administrative)* | Gives Californians rights to know, delete, and opt-out of sale/share of personal data; CPRA strengthens & expands CCPA. | California Privacy Protection Agency (CPPA); CA Attorney General |
|  | **COPPA** — Children’s Online Privacy Protection Act 1998 (USA) *(Civil / Administrative)* | Protects children < 13 online: parental consent, privacy notice, data deletion, safe-harbor program. | Federal Trade Commission (FTC) |
|  | **FERPA** — Family Educational Rights and Privacy Act 1974 (USA) *(Administrative)* | Protects student education records; grants inspection, amendment, and limited disclosure rights. | U.S. Dept. of Education — Family Policy Compliance Office |
|  | **Data-Breach Notification Laws** (All 50 U.S. States, 2002-2018) *(Civil / Administrative)* | Require timely notice to individuals & regulators when PII is compromised; scope & timelines vary by state. | State Attorneys General |
| **Electronic Communications Privacy** | **ECPA** — Electronic Communications Privacy Act 1986 (USA) *(Criminal & Civil)* | Sets warrant / subpoena standards for electronic intercepts (Wiretap Act) & stored data (SCA); pen-register limits. | U.S. DOJ; FBI investigations; federal courts |
| **Electronic Communications** | **CALEA** — Communications Assistance for Law Enforcement Act 1994 (USA) *(Administrative)* | Requires telecom / VoIP providers to build lawful-intercept capabilities. | Federal Communications Commission (FCC); coordination with DOJ/FBI |
|  | **APEC Privacy Framework** *(Voluntary / Guideline)* | Non-binding Asia-Pacific framework for cross-border privacy rules (CBPR); influences national laws & certifications. | APEC economies; CBPR accreditation bodies |
| **Electronic Communications / National Security** | **USA PATRIOT Act 2001** & **USA FREEDOM Act 2015** (USA) *(Criminal & Administrative)* | Expands surveillance, roving wiretaps, “business records” orders; FREEDOM narrows bulk collection. | DOJ / FBI; Foreign Intelligence Surveillance Court (FISC) |
| **Electronic Communications / Cross-Border** | **CLOUD Act 2018** (USA) *(Criminal & Administrative)* | Allows U.S. warrants for data stored abroad by U.S. providers; enables bilateral data-sharing agreements. | U.S. DOJ |
| **Health** | **HIPAA** — Health Insurance Portability & Accountability Act 1996 (USA) *(Administrative & Criminal)* | National standards for PHI privacy, security, & breach notice. | U.S. HHS — Office for Civil Rights (OCR) |
|  | **HITECH Act 2009** (USA) *(Administrative / Civil)* | Strengthens HIPAA for electronic records; makes Business Associates directly liable; 60-day breach notice > 500 records. | HHS-OCR |
| **Finance** | **GLBA** — Gramm-Leach-Bliley Act 1999 (USA) *(Administrative / Civil)* | Requires financial institutions to safeguard customer information & issue privacy notices. | FTC; federal banking regulators (FDIC, Fed, OCC, etc.) |
|  | **SOX** — Sarbanes-Oxley Act 2002 (USA) *(Criminal & Civil)* | Mandates internal controls & truthful financial reporting for public companies; combats corporate fraud. | SEC; Public Company Accounting Oversight Board (PCAOB) |
| **Finance / Government** | **FISMA** — Federal Information Security Modernization Act 2014 (USA) *(Administrative)* | Requires U.S. federal agencies & contractors to run risk-based security programs per NIST guidance. | Office of Management and Budget (OMB); NIST |
| **Payments** | **PCI-DSS** — Payment Card Industry Data Security Standard *(Industry Standard / Contractual)* | Prescribes technical & operational controls for cardholder-data environments; compliance contractual with card brands. | PCI Security Standards Council (PCI SSC) |
| **Export Control** | **EAR** — Export Administration Regulations (USA) *(Criminal & Administrative)* | Controls export/re-export of dual-use items, software & tech. | Bureau of Industry & Security (BIS), U.S. Dept. of Commerce |
|  | **ITAR** — International Traffic in Arms Regulations (USA) *(Criminal & Administrative)* | Regulates export of defense articles & services on U.S. Munitions List. | Directorate of Defense Trade Controls (DDTC), U.S. Dept. of State |
| **Cyber-crime** | **CFAA** — Computer Fraud and Abuse Act 1986 (USA) *(Criminal & Civil)* | Federal anti-hacking law: unauthorized access, damage, fraud. | DOJ / FBI |
|  | **Identity Theft & Penalty Enhancements Act 1998/2004** (USA) *(Criminal)* | Increases penalties for identity theft & aggravated identity theft (up to 15 years). | DOJ / FBI |
| **Trade Secrets / IP** | **Economic Espionage Act 1996** (USA) *(Criminal)* | Criminalizes theft of trade secrets, including industrial espionage for foreign governments. | DOJ / FBI |
| **Critical Infrastructure** | **NERC-CIP** — North American Electric Reliability Corporation Critical Infrastructure Protection Standards *(Administrative)* | Mandatory cyber & physical controls for bulk electric-system operators in North America. | NERC |
| **Constitutional Privacy** | **Fourth Amendment** (U.S. Constitution) *(Constitutional)* | Protects against unreasonable searches & seizures; basis for surveillance-warrant requirements. | Federal & state courts interpret; applies to all U.S. law-enforcement agencies |
| **General Security Framework** | **ISO/IEC 27001** — Information Security Management System Standard *(Industry Standard / Voluntary)* | Certifiable framework for establishing, maintaining & improving an ISMS. | ISO sets standard; accredited certification bodies audit implementers |


### Computer Crime  
- **Why it matters:** CISSP pros must know the legal landscape impacting information security operations and data flows—domestic **and** international.  
- **Key point:** Always recognize when to involve legal counsel; the real skill is knowing the limits of your own expertise.<br>
- The earliest “computer-centric” statutes sought to criminalize hacking‐style activities that didn’t cleanly fit traditional theft or fraud laws.  
- Each U.S. state also has its own computer-crime laws, but Internet incidents typically cross state lines, giving **federal courts** jurisdiction.

- Statutes: **CFAA, DMCA, ECPA (US); CMA 1990 (UK); Budapest Convention**.  
- Offenses: unauthorized access, malware distribution, DDoS, identity theft.  
- Penalties include felony charges, *up to 20 yrs* prison in severe cases.

#### Computer Fraud and Abuse Act (CFAA) — 1986 (original)  
- **Focus:** Federal-interest computers (later broadened), classified info, banking records.  
- **Criminalized:** Unauthorized access, fraud via federal systems, password trafficking, and damage > $5 000.  
- **Exam cue:** First broad U.S. anti-hacking law; foundation for nearly all federal cyber prosecutions.

#### CFAA Amendments (1994 → 2008)
- Added **malicious-code outlaw**, expanded scope to **any computer in interstate commerce**, and allowed **civil suits** by victims.  
- Criticized for over-breadth: violating a website’s Terms of Service **could** be charged as a crime.  
- Recent cases (e.g., *Van Buren* 2021) are narrowing that scope.

#### National Information Infrastructure Protection Act (NIIPA) — 1996
- **Broadened CFAA** to cover computers in **international** commerce.  
- Extended felony penalties to attacks on critical infrastructure (power grids, pipelines, telecom, rail, etc.).

#### Federal Information Security Management Act (FISMA) — 2002
- Mandates **agency-wide information-security programs** for U.S. federal systems and contractor systems.  
- Requires **risk assessments, policies, training, annual testing, incident handling, and continuity planning**.

#### Federal Cybersecurity Laws (Modernization) — 2014
| Law | Core Idea (CISSP view) | Lead Agency |
| ---- | ---------------------- | ----------- |
| **FISMA Modernization Act** | Centralizes most federal cyber-oversight with **DHS**; DoD & Intel remain separate. | DHS |
| **Cybersecurity Enhancement Act** | NIST made the national coordinator for **voluntary standards** (→ NIST CSF). | NIST |
| **National Cybersecurity Protection Act** | Creates NCCIC as the **public/private info-sharing hub** for threats & incidents. | DHS |

#### NIST Special Publications & CSF
- **SP 800-53:** Baseline security & privacy controls for **federal** (and often commercial) systems.  
- **SP 800-171:** Extends similar controls to contractors handling **Controlled Unclassified Information (CUI)**.  
- **Cybersecurity Framework (CSF):** Voluntary, risk-based guidance (Identify, Protect, Detect, Respond, Recover) used globally.

> **Exam-Side Tip:** Be able to pair each law with its primary purpose, scope, and responsible agency—and know that export/import, privacy, and IP laws appear elsewhere in Domain 1.

### Intellectual Property (IP)  
- **Copyright** (software code, docs), **Trademark**, **Patent**, **Trade secret**.  
- Security role: protect employer IP (NDAs, DLP) & avoid infringement.  
- Exam watchword: *“Work for hire”*, *“first-sale doctrine”*, *“fair use”*.

| Law                          | Focus Area                                 | Purpose                                                                                   | Key Provisions                                                                                       | Relevance to CISSP |
|-----------------------------|---------------------------------------------|-------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|---------------------|
| **Lanham Act (1946)**       | Trademark Law                               | Protects trademarks, service marks, and unfair competition                               | - Registration of trademarks<br>- Legal recourse against infringement<br>- Prevention of false advertising | Important for protecting branding and identity integrity; relevant to intellectual property management |
| **Glass–Steagall Act (1933)** | Banking & Financial Regulation              | Separated commercial and investment banking to reduce risk in the financial system       | - Prohibited banks from engaging in investment activities<br>- Established FDIC                         | Less directly CISSP-relevant, but ties to governance, compliance, and financial system protections |
| **Economic Espionage Act (1996)** | Trade Secret Protection & National Security | Criminalizes theft or misappropriation of trade secrets, especially benefiting foreign entities | - Section 1831: Foreign-directed theft<br>- Section 1832: Commercial theft<br>- Applies to individuals and organizations | Highly relevant: protects sensitive information and enforces legal boundaries for data confidentiality |

| Concept | Key Points to Know | Why It Matters for Security Pros |
|---------|--------------------|----------------------------------|
| **Shift to IP-driven economy** | • Services & brand value dominate modern firms  <br>• Intangible assets (logos, names, formulas, creative works) = “IP” | Protecting IP often means protecting *data*: source code, formulas, designs, brand assets. |
| **Copyright** | • Covers *original works of authorship* (8 categories incl. software as “literary works”).  <br>• Protection is automatic at creation; formal registration strengthens enforcement. <br>• Creator holds rights unless it’s a *work for hire*. <br>• Term: Author’s life + 70 yrs (or 95/120 yrs for works-for-hire). | Source code, documentation, videos, training materials all fall under copyright—controls must prevent unauthorized copying. |
| **Digital Millennium Copyright Act (DMCA)** | • 1998 U.S. law aligning with WIPO treaties. <br>• Criminalizes circumvention of copy-protection tech. <br>• Grants “safe-harbor” to ISPs if they meet strict pass-through criteria. <br>• Allows limited backup copies of licensed software, clarifies streaming rules. | Security teams must not build or deploy tools that break DRM; know takedown & notice obligations if hosting content. |
| **Trademarks** | • Protect words, slogans, logos that identify goods/services. <br>• ™ can be claimed upon use; ® requires USPTO registration (<10 yr terms, renewable). <br>• Must not be “confusingly similar” or merely descriptive. | Brand impersonation (phishing, fake apps) violates trademark—security policies should monitor for misuse. |
| **Patents (Utility)** | • 20-year exclusive right to exploit a *new, useful, non-obvious* invention. 20 years from the date the patent is granted.<br>• Software & crypto algorithms can be patented but are controversial. | Assess patent risks when deploying code/algorithms; infringement can halt products. |
| **Design & Plant Patents** | • Design: protects *appearance* (15 yrs).  <br>• Plant: protects engineered species. | Typically less relevant to infosec, but design patents may apply to UI/UX security features. |
| **Software IP Protection Debate** | • Copyright covers expression (code) but **not** underlying ideas. <br>• Patents cover functional ideas but may be too broad. <br>• “Patent trolls” monetize overly broad software patents via lawsuits. | Choose licensing & defensive publication strategies; maintain code secrecy where possible. |
| **Trade Secrets** | • Valuable, non-public business info (formulas, source code, processes). <br>• No registration; protection requires **reasonable secrecy measures** (NDA, need-to-know, access controls). <br>• Protection lasts indefinitely while secrecy is maintained. | Implement DLP, strong IAM, and NDAs; breach could void protection and harm competitiveness. |
| **Economic Espionage Act (1996) & Defend Trade Secrets Act (2016)** | • Criminal penalties up to 15 yrs/$10 M for theft benefiting foreign gov’t; 10 yrs/$5 M otherwise. <br>• 2016 amendment adds federal civil lawsuit option for companies. | Insider-threat monitoring and incident response plans must account for trade-secret theft; federal remedies available. |

| Mark | Name (Symbol) | Indicates | Legal Status / Protection | Typical Use Cases |
|------|---------------|-----------|---------------------------|-------------------|
| © | Copyright symbol | The work is **protected by copyright**. Copyright guards the *expression* of an original creative work (e.g., text, music, art, source code). | Protection is **automatic** as soon as the work is fixed in a tangible form. Registration is *optional* but provides additional legal benefits (statutory damages, attorney’s fees, stronger evidence of ownership). | Books, articles, songs, photographs, software source code, websites, films, artwork, etc. |
| ® | Registered trademark symbol | The word, phrase, logo, design, or other identifier is a **federally registered trademark** (e.g., with the U.S. Patent & Trademark Office). | Only available after **successful registration**. Grants nationwide exclusive rights in the relevant jurisdiction; enables stronger legal remedies against infringers. | Company names (e.g., *Microsoft®*), product names (e.g., *iPhone®*), logos (e.g., Nike Swoosh®), taglines. |
| ™ | Unregistered / common-law trademark symbol | Signals a **claim of trademark rights** that has **not (yet) been federally registered** (or that is registered only at a state level). | Offers “common-law” protection based on **actual use in commerce**. Rights are geographically limited and harder to enforce than a registered mark. | New product names, brand names, slogans, or logos in use but still undergoing or awaiting registration. |
| † | Dagger / obelisk | A **reference mark** (also used for footnotes) or to denote a deceased person in scholarly works. **Not an IP symbol**. | No special legal meaning for intellectual-property purposes. | Footnotes/endnotes in documents (e.g., *† See Appendix A.*), academic or legal citations, obituaries, genealogies. |

> Bottom line:
- A pure algorithm for solving a mathematical problem is not patentable.
- A specific, practical implementation of that algorithm that yields a technical effect may be patent-eligible if the claims are drafted carefully.
- Consult a patent attorney to evaluate novelty, draft claims emphasizing the technical application, and file before any public disclosure.

### Software Licensing  
- Models: **Per-seat, OEM, subscription (SaaS), GPL/MIT (open-source)**.  
- Violations → vendor audits, civil damages, sometimes criminal copyright suits.  
- Understand **shrink-wrap, click-wrap, EULA** enforceability.

### Import/Export  
- Crypto & dual-use tech governed by **EAR, ITAR, Wassenaar**.  
- Key length thresholds (e.g., >56-bit historically restricted).  
- Obtain export licenses; apply geoblocking for sanctioned nations.

| Concept | What you need to know for the exam |
|---------|------------------------------------|
| **Import / Export controls** | U.S. law restricts sending certain hardware, software, technical data, and even PII across borders. Two core rule sets:<br>• **ITAR** – Defense articles/services on the *U.S. Munitions List* (22 CFR 121).<br>• **EAR** – “Dual-use” commercial items on the *Commerce Control List* (Dept. of Commerce / BIS). EAR Category 5 covers **information-security products**, including cryptography. |
| **Countries of Concern** | BIS designates embargoed / high-risk destinations (e.g., **Cuba, Iran, North Korea, Syria**). Exports of high-performance computers or strong crypto to these states normally **require a license or are prohibited**. |
| **Encryption Export Controls** | Historically, strong crypto was almost impossible to export. Current BIS rules create **“retail” / “mass-market”** categories: vendors submit products for a ≤ 30-day review; once approved, items may be exported worldwide except to embargoed countries. Stronger or custom crypto may still fall under EAR 5A002 / 5D002 and need a license. |

> **Exam Tip**: Security professionals must perform **due-diligence and license checks** before shipping equipment, software, or data internationally; negligence can lead to civil or criminal penalties.

### Privacy  
- Global requirements:  
  - **GDPR** (EU) — lawful basis, DPIA, 72-hr breach notice, *up to 4 % global revenue fines*.  
  - **HIPAA** (US health), **GLBA** (US finance), **COPPA**, **FERPA**, **PIPEDA** (CA), **POPIA** (SA).  
- Principles: data minimization, purpose limitation, data-subject rights, transparency.
- **Privacy in the U.S. vs. Europe** – U.S. privacy protections arise piecemeal from court decisions and sector-specific statutes, whereas the EU historically adopts comprehensive, omnibus laws that apply to all personal data.

#### U.S. Privacy Laws  

##### Fourth Amendment  
Guarantees people are secure from unreasonable government searches and seizures; courts extend this to wiretaps and surveillance, providing the constitutional basis for modern privacy claims.

##### United States – Federal Statutes  

| Law / Year | Core Purpose | Key Points |
|------------|--------------|------------|
| **Privacy Act 1974** | Limits what federal agencies may collect and how they disclose personal data | Requires minimal, necessary records; access/amendment rights; only applies to federal agencies |
| **ECPA 1986** | Protects electronic communications content & storage | Criminalizes unauthorized interception/access; covers email, voicemail, mobile calls |
| **CALEA 1994** | Ensures lawful intercept capability | Carriers must build in wire-tap access after court order, regardless of tech |
| **Economic Espionage Act 1996** | Extends theft to include trade secrets | Enables prosecution of industrial espionage |
| **HIPAA 1996** | Safeguards medical information | Privacy & Security Rules, patient rights to access/correct PHI |
| **HITECH 2009** | Modernizes HIPAA, adds breach notification | Business Associates directly liable; 60-day breach notice >500 records |
| **Data Breach Notification Laws** | SB 1386 (CA, 2002) → all 50 states (2018) | Mandate timely notice when PII exposed; details vary by state |
| **COPPA 1998** | Protects children (<13) online | Parental consent, privacy notice, review & deletion rights |
| **GLBA 1999** | Regulates financial-institution privacy | Requires privacy policies, limits data sharing among subsidiaries |
| **USA PATRIOT 2001 / USA FREEDOM 2015** | Expands surveillance powers for national-security purposes | Roving wiretaps, ISP disclosures, enhanced CFAA penalties; provisions repeatedly sunset/renew |
| **CLOUD Act 2018** | Cross-border law-enforcement data access | Allows warrants for data held abroad by U.S. firms; enables bilateral data-sharing pacts |
| **FERPA** | Student educational-record privacy | Inspection/correction rights; limits disclosure without consent |
| **Identity Theft & Penalty Enhancements 1998/2004** | Criminalizes identity theft against individuals | Up to 15-year sentences & fines |

> HIPAA (1996)
- First U.S. law to mandate privacy & security safeguards for Protected Health Information (PHI) held by healthcare entities.  
- Gives patients access/control rights and authorizes HHS/OCR to levy civil & criminal penalties for violations.

> HITECH (2009)
- Strengthens HIPAA for the electronic-records era.  
- Makes Business Associates directly liable and requires breach notices (to individuals + HHS/media if > 500 records) within 60 days.


##### U.S. Workplace Privacy  
Employees have **no reasonable expectation of privacy** on employer-owned devices. Employers should disclose monitoring via contracts, policies, banners, and device labels.

#### European Union Privacy Law

##### European Union GDPR Protection Regulation 2016 → 2018  
- **Applies worldwide** to entities processing EU residents’ data.  
- Core principles: *lawfulness/fairness/transparency*, *purpose limitation*, *data minimization*, *accuracy*, *storage limitation*, *integrity & confidentiality*, *accountability*.  
- **Data subject rights**: access, rectification, erasure (“right to be forgotten”), portability, objection.  
- **Breach notice**: 72 hr to authority.  
- **Cross-border transfers**: Standard Contractual Clauses (SCCs) or Binding Corporate Rules (BCRs); Privacy Shield invalidated by *Schrems II* (2020).

##### 1. EU as Global Privacy Trend-Setter
* **Comprehensive scope** – EU laws regulate *all* personally identifiable info, unlike the U.S. “sectoral” model.  
* **Influence** – EU rules often become de-facto standards for orgs operating worldwide.

##### 2. GDPR (General Data Protection Regulation) – 2016/2018
| Aspect | Summary |
|--------|---------|
| **Purpose** | Replaced 1995 Data Protection Directive to deliver *one harmonized privacy law* across the EU. |
| **Territorial reach** | Applies to any org that *collects* or *processes* EU residents’ data—even if the org is **outside** the EU. |
| **Penalties** | Up to €20 million or 4 % of global turnover for serious violations. |

###### 2.1 Seven Core Principles  
1. **Lawfulness, Fairness, Transparency** – Legal basis + honest disclosures.  
2. **Purpose Limitation** – Collect & process only for stated purposes.  
3. **Data Minimization** – Limit data to what is adequate & relevant.  
4. **Accuracy** – Keep data correct; rectify/erase inaccuracies promptly.  
5. **Storage Limitation** – Retain data only as long as needed; honour the *right to be forgotten*.  
6. **Integrity & Confidentiality** – Apply proper security controls.  
7. **Accountability** – Controller must *prove* compliance (records, DPO, DPIAs, etc.).

##### 3. Cross-Border Data Transfers
| Mechanism | When/How to Use | Notes |
|-----------|-----------------|-------|
| **Standard Contractual Clauses (SCCs)** | Attach EU-approved boiler-plate clauses to contracts moving data out of the EEA. | Quickest path; must use unaltered clauses. |
| **Binding Corporate Rules (BCRs)** | Multinational groups transferring data *internally*. | Lengthy approval by *every* EU DPA where used; suits very large enterprises. |

###### 3.1 End of *Privacy Shield*  
* **Schrems II (2020)** – CJEU invalidated the EU-US Privacy Shield.  
* U.S. firms must now rely on **SCCs** or **BCRs** until a new trans-Atlantic framework is approved.

##### 4. Conflict-of-Laws Scenarios
* U.S. e-discovery demands vs. GDPR restrictions can clash.  
* Always seek specialized counsel to balance competing obligations.

#### APEC Privacy Framework (Asia-Pacific)
* Provides *regional* guidance (notice, choice, security, accountability, etc.) to **facilitate smooth cross-border data flow** among APEC economies.  
* Not legally binding but influences national laws & CBPR certification.

#### Canada – PIPEDA  
Nationwide commercial-sector law governing identifiable personal information. Grants individuals access, correction rights; superseded by “substantially similar” provincial laws (AB, BC, QC). Exempts personal, non-commercial, and government uses.

#### China – PIPL 2021  
First comprehensive Chinese data-protection law:  
- Requires *explicit consent*, *data minimization*, security measures.  
- Establishes rights of access, correction, deletion.  
- Restricts outbound transfers (security assessment, “equivalent protection”).  
- Heavy fines, business suspension, license revocation for violations.

#### South Africa – POPIA 2020  
Eight processing conditions paralleling GDPR. Highlights: consent, purpose specification, special-category & children data controls, Information Regulator enforcement, steep fines/prison for non-compliance.

---

#### State Privacy Laws  

##### CCPA (California) 2018  
- Rights to know, delete, and opt-out of sale of personal info; no retaliation.  
- Inspired similar laws in other states; federal analogue still pending.

States frequently pioneer privacy regulation that later influences nationwide or even federal rules.  
A prime illustration is **California’s Consumer Privacy Act (CCPA)**, enacted in 2018 (GDPR-inspired) and effective as of 2020.

##### Core Rights Granted by the CCPA
1. **Right to Know**  
   *Consumers may request full disclosure of the personal data collected, purposes of use, and third-party sharing.*

2. **Right to Deletion (“Right to be Forgotten”)**  
   *Under defined conditions, individuals can require a business to erase their personal information.*

3. **Right to Opt-Out of Sale**  
   *Individuals may direct a business to stop selling their personal data.*

4. **Right to Non-Discrimination**  
   *Businesses may not retaliate or discriminate against consumers for exercising CCPA rights.*

##### Broader Impact
- California has already expanded the CCPA (e.g., CPRA amendments).  
- Multiple other states (CO, CT, UT, VA, etc.) have introduced similar comprehensive privacy statutes.  
- Organizations operating across the U.S. must now navigate a patchwork of state privacy obligations while anticipating eventual federal harmonization.

---

## Compliance  
**Core idea:**  Demonstrating adherence to statutory, regulatory, and contractual controls to avoid penalties and maintain customer trust.  
- Frameworks: **PCI-DSS, SOX, FISMA, FedRAMP, ISO/IEC 27001, NIST 800-53, COBIT**.  
- Evidence via **audits, SOC 2 reports, continuous monitoring**, GRC tooling.  
- Remember: *Compliance ≠ Security* but synergy is vital for funding and governance.

---

## Contracting and Procurement  
- Insert security clauses into **RFP/SOW/SLA**:  
  - Right-to-audit, breach-notification SLA (<24 hr), data-location, encryption, subcontractor flow-down.  
  - **Termination/exit strategy** for data return & sanitization.  
  - **SBOM** & secure-coding attestations for software supply chain.  
- Evaluate vendor risk with questionnaires, on-site audits, penetration-test attestation.

---

## Summary  
CISSPs must pair technical savvy with legal fluency:

* Differentiate **criminal, civil, administrative** repercussions.  
* Familiarize with major **computer-crime** statutes and **privacy regulations** (GDPR, HIPAA, CCPA).  
* Protect and respect **intellectual property**; manage **software licenses**.  
* Avoid export-control violations for crypto/dual-use tech.  
* Build a **compliance program** that maps controls to multiple frameworks and embeds robust security clauses in contracts.  

Expect exam scenarios on breach-notification timing, cross-border data transfers, IP infringement, and regulatory fines.

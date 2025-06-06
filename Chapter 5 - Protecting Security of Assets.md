# Chapter 5 - Protecting Security of Assets

- [Identifying and Classifying Information and Assets]()
  - [Defining Sensitive Data]()
  - [Defining Data Classifications]()
  - [Defining Asset Classifications]()
  - [Understanding Data States]()
  - [Determining Compliance Requirements]()
  - [Determining Data Security Controls]()
- [Establishing Information and Asset Handling Requirements]()
  - [Data Maintainance]()
  - [Data Loss Prevention]()
  - [Labeling Sensitive Data and Assets]()
  - [Handling Sensitive Information and Assets]()
  - [Data Collection Limitation]()
  - [Data Location]()
  - [Storing Sensitive Data]()
  - [Data Destruction]()
  - [Ensuring Appropriate Data and Asset Retention]()
- [Data Protection Methods]()
  - [Digital Rights Management]()
  - [Cloud Access Security Broker]()
  - [Pseudonymization]()
  - [Tokenization]()
  - [Anonymization]()
- [Understanding Data Roles]()
  - [Data Owners]()
  - [Data Controllers and Processors]()
  - [Data Custodians]()
  - [Users and Subjects]()
- [Using Security Baselines]()
  - [Comparing Tailoring and Scoping]()
  - [Standards Selection]()
- [Summary]()

## Identifying and Classifying Information and Assets  

### Defining Sensitive Data  
- **Sensitive = disclosure, alteration, or loss harms org/individuals.**  
  - PII, PHI, PCI, trade secrets, mission-critical configs.  
- Sensitivity drives **label, handling & retention rules**.

### Defining Data Classifications  
| Gov/Military | Private-Sector (typical) | Notes |
|--------------|-------------------------|-------|
| Top Secret, Secret, Confidential, Unclassified | Restricted, Confidential, Internal, Public | Higher level ⇒ stronger controls & clearance checks |

### Defining Asset Classifications  
- Tangible (servers, laptops) vs **Intangible** (patents, goodwill).  
- Classify on **replacement cost, criticality, legal exposure**.

### Understanding Data States  
- **At Rest, In Transit, In Use.**  
- Map controls: e.g., AES-256 (rest), TLS 1.3 (transit), memory encryption/TEE (use).

### Determining Compliance Requirements  
- Match data type to **GDPR, HIPAA, PCI-DSS, ITAR, SOX** etc.  
- Record of Processing Activities (RoPA) aids audits.

### Determining Data Security Controls  
- Use classification to select **encryption, access control, DLP, retention, shredding**.

---

## Establishing Information and Asset Handling Requirements  

### Data Maintenance  
- Accuracy, timely updates, version control, integrity checks (hash).  

### Data Loss Prevention  
- **Endpoint, network & cloud DLP** to inspect content & enforce policy (block, encrypt, quarantine).

### Labeling Sensitive Data and Assets  
- Clear, human-readable & machine-readable labels; automate via metadata tagging.

### Handling Sensitive Information and Assets  
- Mark, store, transmit, copy & destroy per classification.  
- Least-privilege + need-to-know.

### Data Collection Limitation  
- **Data minimization** principle; capture only what’s necessary & keep no longer than needed.

### Data Location  
- Respect **data residency, sovereignty**; use geofencing or regional cloud.

### Storing Sensitive Data  
- Hardened datacenters, HSMs, KMS, access logging, full-disk crypto, RBAC.

### Data Destruction  
- Clear, purge, destroy; match to media type (degauss, shred, crypto-erase).  
- Maintain **certificates of destruction**.

### Ensuring Appropriate Data and Asset Retention  
- Align with legal retention periods & **records-management schedule**; automate deletion after “dispose-by” date.

---

## Data Protection Methods  

### Digital Rights Management (DRM)  
- Persistently enforces copy/print/view rights; common for media & documents.

### Cloud Access Security Broker (CASB)  
- Visibility & control between users and SaaS: DLP, tokenization, inline encryption, threat prevention.

### Pseudonymization  
- Replace identifiers with **pseudonyms**; reversible with key; keeps analytical value.

### Tokenization  
- Substitute sensitive element (e.g., PAN) with random **token**; original stored in secure vault.

### Anonymization  
- **Irreversibly** remove identifying elements (k-anonymity, differential privacy).  
- Reduces breach liability but can impair utility.

---

## Understanding Data Roles  

| Role | Primary Duties | CISSP Emphasis |
|------|----------------|----------------|
| **Data Owners** | Classify, define protection, approve access | *Ultimate security accountability* |
| **Data Controllers** | Decide purposes/means of processing (GDPR) | Must honor data-subject rights |
| **Data Processors** | Act on behalf of controller; follow instructions | Processor agreements, breach notice duty |
| **Data Custodians** | Day-to-day storage, backup, integrity | Implement owner directives |
| **Users/Subjects** | Access per policy; safeguard creds | Acceptable-use training |

---

## Using Security Baselines  

### Comparing Tailoring and Scoping  
- **Scoping:** include/exclude controls based on system characteristics.  
- **Tailoring:** modify control strength/parameters (e.g., password length).  
- Begin with NIST SP 800-53 or ISO 27002 baseline, then scope & tailor.

### Standards Selection  
- Map chosen controls to **legal, contractual, industry** drivers (PCI, FISMA, CIS).  
- Reference architectures & benchmarks (CIS-CAT, DISA STIGs).

---

## Summary  
Asset protection starts with **proper classification** and **role assignment**, then layers technical & administrative controls across **data states**. Key CISSP exam themes:

* Understand **classification schemes** & how they dictate handling/destruction.  
* Recognize data-protection techniques (DLP, tokenization, DRM, CASB).  
* Distinguish **pseudonymization vs anonymization** and related compliance impacts.  
* Apply **scoping/tailoring** to security baselines for pragmatic, risk-aligned control sets.  

Master these concepts to answer scenario questions on safeguarding information assets end-to-end.


# Chapter 14: Controlling and Monitoring Access

- [Comparing Access Control Models](#comparing-access-control-models)
  - [Comparing Permissions, Rights, and Privileges](#comparing-permissions-rights-and-privileges)
  - [Understanding Authorization Mechanisms](#understanding-authorization-mechanisms)
  - [Defining Requirements with a Security Policy](#defining-requirements-with-a-security-policy)
  - [Introducing Access Control Models](#introducing-access-control-models)
  - [Discretionary Access Control](#discretionary-access-control)
  - [Nondiscretionary Access Controls](#nondiscretionary-access-controls)
- [Implementing Authentication Systems](#implementing-authentication-systems)
  - [Implementing SSO on the Internet](#implementing-sso-on-the-internet)
  - [Implementing SSO on Internal Networks](#implementing-sso-on-internal-networks)
- [Zero-Trust Access Policy Enforcement](#zero-trust-access-policy-enforcement)
- [Understanding Access Control Attacks](#understanding-access-control-attacks)
  - [Risk Elements](#risk-elements)
  - [Common Access Control Attacks](#common-access-control-attacks)
  - [Core Protection Methods](#core-protection-methods)
- [Summary](#summary)

## Comparing Access Control Models

### Comparing Permissions, Rights, and Privileges
| Term | What It Controls | Typical Example | Exam Hint |
|------|------------------|-----------------|-----------|
| **Permissions** 🔑 | Actions on **objects** | *Read*, *Write*, *Execute* on a file | Think **“file-centric”** capabilities |
| **Rights** 🛠️ | System-level **actions** | *Change system time*, *Restore backups* | Often tied to **OS roles** |
| **Privileges** 🎖️ | **Combination** of permissions **&** rights | Full **Administrator** access | Remember “**elevated**” authority |

*Key Point*: Privileges ⊇ Rights ⊇ Permissions—the higher term subsumes the lower ones.

### Understanding Authorization Mechanisms
| Mechanism | Purpose | CISSP Takeaway |
|-----------|---------|---------------|
| **Implicit Deny** | Block by default unless explicitly allowed | “Deny all unless…” is the safest rule |
| **Access Control Matrix** | Central table mapping **subjects ↔ objects** | Conceptual model behind ACLs |
| **Capability List** | **Subject-focused** list of allowed objects | Decentralized; think “token” |
| **Constrained Interface** | Hide/disable UI elements a subject can’t use | Enforces *least privilege* visually |
| **Content-Dependent Control** | Filter data based on **fields/content** | Ex: DB **views** that mask PII |
| **Context-Dependent Control** | Grant access only after specific **workflow** or **time** | Shopping-cart checkout, time-of-day rules |
| **Need to Know** | Limit data access to job-related info | Often paired with MAC labels |
| **Least Privilege** | Grant **minimum** rights to perform duties | Prevents privilege creep |
| **Separation of Duties** | Split sensitive tasks among ≥2 people | Mitigates fraud/errors |

### Defining Requirements with a Security Policy
* A **security policy** is senior management’s high-level directive that defines **what** must be protected and **to what extent**.  
* It guides the creation of **standards (what)**, **procedures (how)**, and **guidelines (best practices)**.  
* For access control, the policy should state principles such as **least privilege**, **need to know**, and **separation of duties**—implementation details reside in lower-level documents.

### Introducing Access Control Models
| Model | Core Idea | Strengths | Weaknesses | Typical Environment |
|-------|-----------|-----------|------------|---------------------|
| **Discretionary (DAC)** | **Owner** decides who accesses the object | Flexible; easy delegation | Susceptible to insider misconfiguration | Windows **NTFS** ACLs |
| **Role-Based (RBAC)** | Rights tied to **job roles/groups** | Simplifies admin; curbs privilege creep | Roles must stay current | Enterprise apps, AD groups |
| **Rule-Based** | Global **if–then rules** | Consistent, easy to audit | Coarse-grained | Firewalls, routers |
| **Attribute-Based (ABAC)** | Policies evaluate **multiple attributes** (user, device, action, context) | Highly granular, dynamic | Complex to design | SDN, cloud IAM |
| **Mandatory (MAC)** | **Labels** on subjects & objects; clearance must dominate classification | Strong confidentiality | Rigid; admin overhead | Military, govt |
| **Risk-Based** | Real-time risk scoring drives decisions | Adaptive; leverages ML | Still evolving; opaque logic | Zero-trust, adaptive MFA |

### Discretionary Access Control
* **Ownership-centric**—object creator controls its ACL.  
* Implemented via **identity-based ACLs**; owners can **delegate** rights.  
* **Flexible** but prone to **privilege sprawl** and **weak audit trails**.  
* Windows file permissions are classic DAC.  
* Exam angle 🔍: Know that **DAC ≠ RBAC**; DAC is “you created it, you share it.”

### Nondiscretionary Access Controls
* **Centrally managed**; users can’t change permissions on their own.  
* Includes **RBAC, MAC, Rule-Based, ABAC, Risk-Based** models.  
* Advantages: **Consistency, easier auditing, policy enforcement**.  
* Drawback: **Less flexibility** for data owners; requires robust administration.  

*Remember*: “Non-DAC” essentially means **any model where access decisions are **not** left to individual resource owners**.

## Implementing Authentication Systems

### Implementing SSO on the Internet  

#### Extensible Markup Language (XML)  
* **What it is**: A meta-language that lets organizations tag data with custom, self-describing elements.  
* **Why it matters**: Most web-SSO protocols—SAML, SOAP, WS-Federation—are **XML-based**, enabling cross-vendor interoperability.

#### Security Assertion Markup Language (SAML) 🔑  
| Element | Role in the Flow | Exam Keywords |
|---------|------------------|---------------|
| **Principal / User Agent** | Browser or app initiating access | “End-user” |
| **Service Provider (SP)** | Hosts the target service | “Relying party” |
| **Identity Provider (IdP)** | Authenticates user, issues **assertions** | “Asserting party” |
| **Assertion Types** | *Authentication*, *Attribute*, *Authorization* | XML messages signed by IdP |

* SAML 2.0 = *XML standard* (OASIS) for **web browser SSO**.  
* Uses **POST**/Redirect bindings; relies on **X.509**-signed XML.  
* Strength: Full **AA** (authentication & authorization) statements; works across disparate organizations (federation).

#### OAuth 2.0 🔓  
* **Framework** (RFC 6749) for **authorization**, not authentication.  
* Issues **access tokens** allowing a client app to call an API on the user’s behalf—credentials are never shared with the third party.  
* Flow examples: *Authorization Code*, *Client Credentials*, *Device Code*.  
* Tokens are bearer-style; typical lifetime is **minutes to hours**.

#### OpenID Connect (OIDC) 🛰️  
* Adds an **authentication layer** on top of OAuth 2.0.  
* IdP returns a **JSON Web Token (JWT)** called an **ID Token** containing the user’s identity plus optional profile claims.  
* Enables social-login flows like “Sign in with Google.”

#### Comparing SAML, OAuth, and OIDC  
| Feature | SAML 2.0 | OAuth 2.0 | OpenID Connect |
|---------|----------|-----------|----------------|
| **Primary Purpose** | Auth + AuthZ | AuthZ only | Auth + AuthZ |
| **Data Format** | XML | JSON (HTTP) | JSON (JWT) |
| **Token Type** | XML Assertion | Access Token | ID Token (JWT) + Access Token |
| **Common Use-Case** | Enterprise federation / SSO between orgs | Mobile & API access delegation | Social login, modern web/mobile SSO |
| **Transport** | Browser Redirect/POST | RESTful APIs | RESTful APIs |
| **Backward-Compatibility** | Mature but verbose | Lightweight; many grants | Depends on OAuth 2.0 |

> **Exam Cue**: Remember “OAuth = *authorization*; OIDC = *OAuth + authentication*; SAML = XML-based legacy-friendly federation.”  

### Implementing SSO on Internal Networks  

#### AAA Protocols Overview  
AAA = **Authentication**, **Authorization**, **Accounting**—the pillar trio for network access control.

| Protocol | Transport / Port | Strengths | Limitations | Typical Use |
|----------|-----------------|-----------|-------------|-------------|
| **Kerberos** | UDP/TCP 88 | Mutual auth, *tickets*, **SSO**; encrypts credentials (AES) | KDC = single point of failure; strict time sync (±5 min) | Windows/AD domain logon, Unix realms |
| **RADIUS** | UDP 1812/1813 (TLS → TCP 2083) | Widely supported NAS/VPN; centralized AAA | Encrypts only password by default; UDP = no delivery guarantee | ISP dial-in, 802.1X Wi-Fi, VPN concentrators |
| **TACACS+** | TCP 49 | Separates A-A-A; encrypts **entire** payload; command-by-command auth | Cisco-centric heritage; heavier than RADIUS | Device administration (routers/switches), high-security NAS |

#### Kerberos  
* **Key Distribution Center (KDC)** issues:  
  * **Authentication Service (AS)** → verifies user & gives **Ticket-Granting Ticket (TGT)**.  
  * **Ticket-Granting Service (TGS)** → swaps TGT for **Service Ticket** to a resource.  
* **Tickets**: time-stamped, encrypted blobs proving identity; prevent **replay attacks**.  
* **Realm**: Administrative domain under one KDC. Trusts can link realms for cross-domain SSO.  
* **Process Recap**: Logon → TGT → per-service ticket → mutual authentication between client & server.

#### RADIUS  
* Client = **Network Access Server (NAS)**; Server = RADIUS.  
* Workflow: NAS forwards credentials → RADIUS validates → returns **Access-Accept/Reject** & attributes (e.g., VLAN).  
* Supports **callback** or **location-based** policies.  
* Accounting records (start, stop, usage) aid auditing and billing.

#### TACACS+  
* Splits Authentication, Authorization, Accounting into **independent daemons**—flexible deployment.  
* **Full-packet encryption** (unlike RADIUS).  
* Can authorize individual device-level commands—granular for network gear administration.  
* Reliable **TCP** transport reduces lost records.

### Quick Reference Table – Internet vs. Internal SSO Mechanisms

| Environment | Protocol(s) | Key Token | Core Benefit | Exam Tip |
|-------------|-------------|-----------|--------------|----------|
| **Internet / Cloud** | SAML, OAuth, OIDC | XML Assertion / JWT | Cross-domain federation without sharing passwords | *SAML = XML; OAuth = token delegation; OIDC = OAuth + ID* |
| **Enterprise LAN / VPN** | Kerberos, RADIUS, TACACS+ | Ticket / Access-Accept | Centralized AAA & single credential set | *Kerberos requires synced clocks; TACACS+ encrypts full payload* |

## Zero-Trust Access Policy Enforcement  

### Core Principles  
| Principle | Key Idea | CISSP Angle |
|-----------|----------|-------------|
| **Never Trust, Always Verify** 🔍 | No implicit trust based on network location; every request is authenticated and authorized in real time. | Defeats perimeter-only “moat & castle.” |
| **Continuous Evaluation** | Identity, device posture, location, time, workload sensitivity, and threat intel are checked **every** time. | Dynamic, risk-adaptive controls. |
| **Least Privilege / Micro-Segmentation** | Users & workloads get only the minimum access, scoped to *single* resources. | Stops lateral movement. |

#### NIST ZTA Logical Components  
| Component | What It Does | Example Technologies |
|-----------|--------------|----------------------|
| **Policy Engine** | Runs trust algorithm; decides *allow/deny/revoke* | PDP logic in ZTNA, SDP controllers |
| **Policy Administrator** | Enforces PE decisions; issues session creds/tokens | Cloud proxy, micro-gateway |
| **Policy Enforcement Point (PEP)** | Intercepts traffic, queries PA, applies verdict | Host agent + inline gateway |
| **External Data Feeds** | Supply context (identity, posture, SIEM, threat intel) | IdP, MDM/UEM, EDR, TI feeds |

> **Exam cue**: PE + PA = **Policy Decision Point (PDP)**; PEP = **Policy Enforcement Point**.

## Understanding Access Control Attacks  

### Risk Elements  
| Term | Definition | Quick Mnemonic |
|------|------------|----------------|
| **Threat** | Potential event with adverse impact | “*Actor or act*” |
| **Vulnerability** | Weakness exploitable by a threat | “*Door left open*” |
| **Risk** | Likelihood × impact of threat exploiting vulnerability | “*What can go wrong & hurt*” |

### Common Access Control Attacks  

#### Privilege Escalation  
| Type | Direction | Typical Tactic |
|------|-----------|----------------|
| **Horizontal** | Same privilege level → another account | Pass compromised user creds to peer machine |
| **Vertical** | Low → high privilege (e.g., admin) | Exploit vuln / token abuse / Mimikatz |

#### Password-Focused Attacks  
| Attack | Core Method | Mitigation Snapshot |
|--------|-------------|---------------------|
| **Dictionary** | Compare hashes against common-word list | Long passphrases, salting |
| **Brute-Force** | Try *all* combos | Length ↑, charset ↑, rate-limit |
| **Spraying** | Same pwd vs many accounts to dodge lockout | MFA, lockout by *IP* |
| **Credential Stuffing** | Reuse pw/username pair on many sites | Unique passwords, breach monitoring |
| **Birthday (Collision)** | Find diff pwd with same hash | Use collision-resistant hashes (SHA-3) |
| **Rainbow Table** | Pre-computed hash lookup | Salt + pepper, strong KDF (Argon2/bcrypt) |

#### Hash / Ticket Abuse  
| Technique | Target | Tooling |
|-----------|--------|---------|
| **Pass-the-Hash (PtH)** | NTLM hash → NTLM auth | Mimikatz, WCE |
| **Overpass-the-Hash** | NTLM hash → Kerberos TGT | Rubeus |
| **Pass-the-Ticket** | Inject Kerberos TGT/TGS | Rubeus, Mimikatz |
| **Silver Ticket** | Forge TGS for service account | Mimikatz |
| **Golden Ticket** | KRBTGT hash → forge any TGT | Mimikatz |

#### Kerberos-Specific Roasting & Brute  
| Attack | Vulnerable To | Goal |
|--------|---------------|------|
| **AS-REP Roast** | Users w/o pre-auth | Crack `AS-REP` ciphertext offline |
| **Kerberoasting** | Weak service-acct keys | Crack TGS hash to own service acct |
| **kerbrute.py / Rubeus brute** | Username enumeration | Online user/password discovery |

#### Network & Identity Deception  
* **Sniffer / Eavesdropping**: Capture cleartext creds with Wireshark.  
* **Spoofing**: Impersonate IP, email, or caller-ID to harvest creds or bypass ACLs.

### Core Protection Methods  
* **Physical & logical access controls** on servers storing credential DBs.  
* **Strong salted & peppered hashes**: Argon2, bcrypt, PBKDF2.  
* **MFA everywhere**—defeats single-factor compromise.  
* **Account lockout + anomaly detection** (clip levels, geo-velocity).  
* **Secure protocols** (HTTPS, SSH, TLS) & encryption in transit.  
* **Patch & harden services**; run with least-privilege service accounts (avoid `LocalSystem`).  
* **Log & monitor** (SIEM, EDR) for Mimikatz signatures, unusual ticket requests.  
* **User education** on unique passphrases, phishing awareness.  

## Summary  

* Zero-trust **eliminates implicit trust**, requiring continuous, context-rich policy checks via PDP and PEP components.  
* Access control attacks range from **privilege escalation** (horizontal/vertical) and **password/credential cracking** (dictionary, brute, spraying, rainbow) to sophisticated **hash/ticket forgeries** (PtH, Golden Ticket) and **network sniffing/spoofing**.  
* **Defense-in-depth** against these threats leverages strong cryptography, MFA, rigorous monitoring, least privilege, and user/administrator hygiene.



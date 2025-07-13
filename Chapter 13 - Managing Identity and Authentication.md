# Chapter 13: Managing Identity and Authentication

- [Study Essentials](#study-essentials)
- [Controlling Access to Assets](#controlling-access-to-assets)
  - [Controlling Physical and Logical Access](#controlling-physical-and-logical-access)
  - [The CIA Triad and Access Controls](#the-cia-triad-and-access-controls)
- [The AAA Model](#the-aaa-model)
  - [Identification and Authentication Strategy](#identification-and-authentication-strategy)
  - [Comparing Subjects and Objects](#comparing-subjects-and-objects)
  - [Registration, Proofing, and Establishment of Identity](#registration-proofing-and-establishment-of-identity)
  - [Authorization and Accounting](#authorization-and-accounting)
  - [Authentication Factors Overview](#authentication-factors-overview)
  - [Something You Know](#something-you-know)
  - [Something You Have](#something-you-have)
  - [Something You Are](#something-you-are)
  - [Multifactor Authentication (MFA)](#multifactor-authentication-mfa)
  - [Passwordless Authentication](#passwordless-authentication)
  - [Device Authentication](#device-authentication)
  - [Service Authentication](#service-authentication)
  - [Mutual Authentication](#mutual-authentication)
- [Implementing Identity Management](#implementing-identity-management)
  - [Single Sign-On](#single-sign-on)
  - [SSO and Federated Identities](#sso-and-federated-identities)
  - [Credential Management Systems](#credential-management-systems)
  - [Credential Manager Apps](#credential-manager-apps)
  - [Scripted Access](#scripted-access)
  - [Session Management](#session-management)
- [Managing the Identity and Access Provisioning Life Cycle](#managing-the-identity-and-access-provisioning-life-cycle)
  - [Provisioning and Onboarding](#provisioning-and-onboarding)
  - [Deprovisioning and Offboarding](#deprovisioning-and-offboarding)
  - [Role Definition and Transition](#role-definition-and-transition)
  - [Account Maintenance](#account-maintenance)
  - [Account Access Review](#account-access-review)
- [Summary](#summary)

## Study Essentials
Identity and Access Management (IAM) 🛡️ is the domain that **grants, monitors, and revokes** privileges for users, devices, and services.  
Chapter 13 (with Chapter 14) focuses on the **AAA model—Authentication, Authorization, and Accounting**, ensuring that only the right **subjects** reach the right **objects** in a verifiable way. Mastery of these fundamentals underpins every control you will see on the CISSP exam.

## Controlling Access to Assets
Access controls protect **tangible** (servers, devices, facilities) and **intangible** (data, intellectual property) assets.

### Controlling Physical and Logical Access
| Control Type | Goal | Typical Examples | CISSP Tip |
|--------------|------|------------------|-----------|
| **Physical** | Block unauthorized entry, secure environment | Fences, gates, locks, CCTV, HVAC, fire suppression | “Touch-able” controls; detailed in Chapter 10 |
| **Logical**  | Verify identity, limit system/data use    | Passwords, biometrics, ACLs, permissions, encryption | Often called *technical* controls |

> 🔍 **Remember:** Physical controls protect the hardware that logical controls depend on. Both are tested together.

### The CIA Triad and Access Controls
| Principle | What Access Controls Prevent | Common Exam Keywords |
|-----------|-----------------------------|----------------------|
| **Confidentiality** 🔒 | Unauthorized **viewing** of data | Encryption, need-to-know, classification |
| **Integrity** 🧩 | Unauthorized **modification** of data/configs | Hashing, version control, change mgmt |
| **Availability** ⏱️ | Disruption of **legitimate** access | Redundancy, backups, failover |

## The AAA Model
#### Big Picture
1. **Authentication** – Prove identity  
2. **Authorization** – Grant appropriate privileges  
3. **Accounting** – Record and review activity  

### Identification and Authentication Strategy
* **Identification** = “I am _Alice_”  
* **Authentication** = “Here is my 🔑 to prove it”  
* Both occur together; uniqueness of IDs is essential.  
* Credentials must be protected (e.g., hashed passwords).

### Comparing Subjects and Objects
| Term | Definition | Exam Example |
|------|------------|--------------|
| **Subject** | Active entity requesting data | User, process, service |
| **Object**  | Passive entity containing data | File, DB record, printer |
| **Access**  | Flow of info **object ➡️ subject** | Read a file, query DB |

> Tip: A web app can **switch roles**—object when serving pages, subject when pulling a cookie.

### Registration, Proofing, and Establishment of Identity
* **In-person proofing**: passport/ID checked by HR.  
* **Remote proofing**: Knowledge-Based Authentication (KBA) questions.  
* **Cognitive passwords** (security questions) are weak—NIST discourages static Q&A due to social-media exposure.  
* Biometric enrollment = capture & store reference template.

### Authorization and Accounting
* **Authorization**: Enforces **least privilege**—permissions mapped to proven ID.  
* **Accounting**: Audit logs ➡️ non-repudiation & policy compliance.  
  * “All-or-nothing” auth vs. *granular* authorization.

### Authentication Factors Overview
| Factor | AKA (legacy) | Typical Methods | Strength |
|--------|--------------|-----------------|----------|
| **Something You Know** | Type 1 | Password, PIN, passphrase | Weakest |
| **Something You Have** | Type 2 | Smartcard, OTP token | Medium |
| **Something You Are** | Type 3 | Biometrics (fingerprint, iris) | Strongest |
| *Attributes* | — | Somewhere You Are, Context-aware, Something You Do | Adaptive |

*Single-factor* uses one; **MFA** uses ≥2 different factors.

---

### Something You Know
* **Passwords** are *static* and vulnerable to brute force, spraying, and credential stuffing.  
* **Passphrases** boost length & memorability.  
* **PINs**: numeric, often used on smartcards or mobile devices.

#### Password Policy Components
| Setting | Purpose |
|---------|---------|
| **Max Age** | Force periodic change (except where NIST says otherwise) |
| **Complexity** | Mix of char types |
| **Length** | ≥ 8 (NIST); ≥ 12 (PCI DSS) |
| **Min Age** | Block rapid cycling back to old pw |
| **History** | Remember last _n_ passwords |

#### NIST vs PCI DSS Requirements
| Requirement | **NIST 800-63B** | **PCI DSS 4.0** |
|-------------|-----------------|-----------------|
| Expiration  | Only if compromised | Every 90 days |
| Min Length  | 8–64 chars | 12+ chars |
| Special Chars | Not required | Must include alpha & numeric |
| Screen vs common pw list | ✅ | (Not specified) |

### Something You Have
#### Smartcards
* Chip‐enabled ID containing certificates.  
* Require **PIN+card** → MFA.

#### Authenticators / Tokens
| Method | Clock? | OTP Lifetime | RFC |
|--------|--------|-------------|-----|
| **TOTP** ⏲️ | Yes | 30-60 s | 6238 |
| **HOTP** 🔢 | No (counter) | Until used | 4226 |

> 💡 Hardware failure, loss, or battery death = availability risk.

### Something You Are
#### Common Biometrics
| Modality | Accuracy | Notes |
|----------|----------|-------|
| **Retina** 👁️ | Highest | Privacy concerns; 3 in. range |
| **Iris** 👀 | Very high | 20–40 ft; can be spoofed with image |
| **Fingerprint** 🖐️ | High | Consumer devices; minutiae matching |
| **Palm Vein** ✋ | High | Near-infrared vein scan |
| **Face** 🙂 | Moderate | Used in mobile unlock, border control |
| **Voiceprint** 🎤 | Lower | Affected by illness, environment |

#### Error Metrics
| Metric | What It Measures | Alias |
|--------|------------------|-------|
| **FRR** | Valid user rejected | Type I error |
| **FAR** | Impostor accepted | Type II error |
| **CER** | Point where FRR = FAR | Lower CER = better |

Additional considerations:
* **Enrollment time** ≤ 2 min preferred.  
* **Throughput rate** ≤ 6 s for user acceptance.  
* Sensitivity tuning: raising sensitivity ↓FAR but ↑FRR—choose based on risk appetite (e.g., secure vault favors low FAR).

### Multifactor Authentication (MFA)

**Definition**  
MFA requires two **or more different authentication factors** (e.g., *something you know* + *something you have*). Two-factor authentication (2FA) is the simplest form of MFA. Using two methods from the *same* factor (e.g., password + PIN) **is NOT MFA**.

| Factor Category | Typical Mechanisms | Common Threats | Exam Note |
|-----------------|--------------------|----------------|-----------|
| Something You Know | Password, PIN, passphrase | Brute-force, phishing | Weakest factor |
| Something You Have | Smartcard, OTP token, hardware passkey | Theft, cloning | SMS OTP is **deprecated** by NIST 800-63B 📵 |
| Something You Are | Fingerprint, iris, facial scan | Spoofing, sensor bypass | Strongest factor |
| Somewhere You Are / Do | Geolocation, gestures | GPS spoofing | Context-aware, adaptive |

**Security Benefit** 🛡️  
An attacker must compromise *all* factors—raising the difficulty exponentially.

> **CISSP Tip:** MFA strength comes from *factor diversity*, not sheer number of steps.

### Passwordless Authentication

**Concept**  
Eliminates memorized secrets. Users authenticate with hardware tokens, biometrics, or cryptographic “passkeys” compliant with **FIDO2/WebAuthn** standards.

| Approach | How It Works | Pros | Cons/Challenges |
|----------|--------------|------|-----------------|
| Biometric unlock (face, fingerprint) | Device stores private key in Trusted Platform Module (TPM) and signs a challenge | User convenience 😊 | Sensor spoofing, device loss |
| Hardware passkey (e.g., YubiKey) | Asymmetric key pair; user taps device to sign | Phishing-resistant | Cost, user training |
| Platform passkey (synced via cloud) | Private key split & escrowed among secure enclaves on user devices | Seamless cross-device | Vendor lock-in, recovery complexity |

**Why It Matters for the Exam**  
Password fatigue → risky behavior → breaches. Passwordless mitigates these user-centric weaknesses while supporting MFA (e.g., device + biometric).

### Device Authentication

Identifies and validates **endpoint devices** before network or application access.

| Technique | Description | Typical Use |
|-----------|-------------|-------------|
| Device fingerprinting | Browser/OS attributes (fonts, plug-ins, timezone, etc.) hashed into a unique ID | Web apps, risk-based auth |
| 802.1X | Port-based NAC enforcing EAP methods | Wired/wireless LAN |
| MDM + NAC | Mobile posture checks (OS version, jailbreak) | BYOD environments |
| Certificates | X.509 issued to device; TLS mutual auth | VPN, IoT |

> **Exam Angle:** Device auth complements user auth—both are needed to stop rogue endpoints.

### Service Authentication

Services (daemons, scheduled jobs, APIs) use *service accounts* or certificates to prove identity.

* **Service Account Hardening**
  * Long, complex password 🔑
  * “Password never expires” avoided—use managed rotation tools
  * Non-interactive logon flag set
* **Certificate-Based Service Auth**
  * Mutual TLS between microservices
  * API keys with short TTLs + scopes

**Audit Concern**  
Service accounts often have elevated privileges. Regular **account access reviews** catch stale or over-privileged services.

### Mutual Authentication

Both entities **authenticate each other** to prevent man-in-the-middle attacks.

| Scenario | Mechanism | Example |
|----------|-----------|---------|
| Client–Server | TLS with client certificates | Remote VPN connection |
| Peer-to-Peer | Kerberos AP-REQ / AP-REP messages | Internal Windows domain comms |
| API-to-API | OAuth 2.0 mTLS or signed JWTs | Microservice mesh |

Failure to authenticate either side terminates the session—protecting credentials from rogue endpoints.

### Implementing Identity Management

Centralized vs. decentralized architectures govern how identities and authorizations are stored and verified.

#### Single Sign-On

*Authenticate once, access many resources.*

| Benefit | Risk | Mitigation |
|---------|------|------------|
| Fewer passwords → less reuse/writing | Single credential = single point of failure | MFA, session time-outs |
| Streamlined provisioning | Wide breach blast radius | Strong logging & anomaly detection |

Common protocols: **Kerberos, LDAP bind, SAML, OAuth/OIDC, Kerberos-based AD SSO**.

#### SSO and Federated Identities

Single Sign-On (SSO) lets a user **authenticate once** and then reuse that assertion across multiple applications or systems 🗝️.  
Federated Identity Management (FIM) extends this concept **across organizational boundaries**, mapping an internal identity to a shared **federated ID** that partner systems trust.

##### Why It Matters
| Benefit | Exam Lens | Caveat |
|---------|-----------|--------|
| Fewer credentials → less password fatigue | Usability vs. security trade-off | If SSO token is stolen, attacker gains broad access |
| Transparent access to partner resources | *Security Architecture & Engineering* + *IAM* domains | Each resource owner still defines its own authorization policies |
| Centralized auditing | Supports non-repudiation | Requires robust logging infrastructure |

##### Components & Protocols
| Layer | Purpose | Common Protocols / Standards |
|-------|---------|------------------------------|
| **Assertion** | Carry identity & attributes | SAML 2.0 (XML), OIDC (JSON/JWT) |
| **Authorization** | Delegate access via tokens | OAuth 2.0 (Bearer, mTLS, JWT) |
| **Trust Framework** | Define legal & technical rules | Federation agreements, metadata exchange |

##### Federation Deployment Models
| Model | Where IdP Lives | Typical Use Case | Control Level | Latency |
|-------|-----------------|------------------|---------------|---------|
| **Cloud-Based Federation** ☁️ | Third-party IdP | SaaS training portal, HR benefits | Low (outsourced) | Depends on provider |
| **On-Premises Federation** 🏢 | Inside each org’s DC | M&A between two companies | High (full admin) | LAN-speed |
| **Hybrid Federation** 🔄 | Mix of on-prem & cloud | Gradual cloud migration | Medium | Variable |

> **Exam Tip:** Federation ≠ automatic access to everything. Each service owner still enforces **least privilege**.

##### Cloud-Based Federation
* External IdP (e.g., Okta, Azure AD) holds federated IDs.  
* Internal login ID → mapped to federated ID → SAML/OIDC assertion to SaaS.  
* Fast to deploy; dependency on provider uptime and SLAs.

##### On-Premises Federation
* Internal IdP servers exchange trust metadata (certs, endpoints).  
* Ideal for organizations needing strict data residency or custom workflows.  
* Acts as an SSO “bridge” after mergers.

##### Hybrid Federation
* Combine on-prem IdP with cloud IdP to cover all apps.  
* Enables phased migration or multi-cloud strategy.  
* Careful token/cookie domain scoping required.

##### Just-in-Time (JIT) Provisioning
| Step | Action |
|------|--------|
| 1 | User authenticated in home IdP |
| 2 | First visit to service provider (SP) triggers SAML/OIDC assertion |
| 3 | SP auto-creates local account with received attributes | 
| 4 | User gains immediate access without help-desk ticket 💡 |

*Reduces administrative overhead* but relies on accurate attribute mapping (e.g., `email`, `role`).

##### Exam Checkpoints
* Know how **SAML, OAuth, and OIDC** differ (assertion vs. delegation vs. authentication layer).  
* Understand that **federated ID** is a *reference token*—not necessarily the same as local username.  
* JIT ≠ full provisioning lifecycle; off-boarding still required to avoid orphaned access.  
* SSO tokens must be protected (TLS, short TTL, secure cookies) to maintain **Confidentiality** and **Integrity** of the assertion.

#### Credential Management Systems

Enterprise or browser-integrated vaults that store credentials encrypted at rest.

| Feature | Security Point |
|---------|----------------|
| Auto-fill / auto-login | Beware of click-jacking |
| Master secret / hardware-backed key | Single point requiring strong protection |
| API (W3C Credential Management) | Enables federated IdP pickup |

IDaaS = **Identity as a Service**—cloud-hosted IAM delivering SSO/MFA.

#### Credential Manager Apps

User-side password vaults (e.g., Windows Credential Manager, KeePass, 1Password).

* Store secrets in encrypted DB (AES‐256).  
* Recommend unique passphrase master key + MFA unlock.

#### Scripted Access

Logon scripts or automation tools inject credentials for legacy systems lacking SSO.

*Advantages:* Simulates SSO where none exists.  
*Risks:* Credentials often stored in **cleartext**—restrict file ACLs & use secure vault references.

#### Session Management

Controls for *post-authentication* lifecycle.

| Control | Desktop Example | Web Example |
|---------|-----------------|-------------|
| Idle lockout | Screen saver lock after 15 min | HTTP session cookie timeout |
| Absolute timeout | Forced logoff after 8 hr shift | JWT exp/nbf claims |
| Re-auth for sensitive ops | UAC prompt in Windows | Re-enter password for bank transfer |

Secure frameworks enforce **TLS**, use random session IDs, and rotate IDs after privilege elevation.

## Managing the Identity and Access Provisioning Life Cycle

The provisioning life cycle 🔄 governs **creation, use, review, and retirement** of every identity (user, device, service) that can access organizational assets. Proper lifecycle controls underpin CIA, least privilege, and non-repudiation on the CISSP exam.

### Provisioning and Onboarding

| Step | Key Activities | Exam Pointers |
|------|---------------|---------------|
| **Identity Proofing** | Validate hire via photo ID, background/credit checks, clearance verification | NIST 800-63A assurance levels |
| **Account Enrollment** | Create unique username; capture required attributes (name, email, biometrics) | Automation ensures naming consistency |
| **Privilege Assignment** | Map user to roles/groups → inherited permissions | *Role-Based Access Control (RBAC)* best practice |
| **Asset Issuance** | Laptops, smartcards, OTP tokens recorded in inventory | Chain-of-custody logs |
| **Onboarding Brief** | AUP signature ✍️, security awareness, help-desk procedures | CISSP stresses people + process |

> **Tip:** Automated provisioning tools reduce human error and support *just-enough* access from day one.

### Deprovisioning and Offboarding

| Task | Rationale | Pitfalls |
|------|-----------|----------|
| **Disable (then delete) account** | Prevents logon while preserving data for review | Immediate deletion may orphan encrypted files |
| **Recover/transfer data** | Manager reviews mailboxes, files, encryption keys 🔑 | Plan for personal vs corporate data segregation |
| **Revoke credentials & access tokens** | Blocks SSO, VPN, cloud apps | API keys, certificates often forgotten |
| **Asset return** | Laptop, mobile, passkeys—verify against inventory | Loss inflates risk & costs |
| **Terminate benefits** | Stop payroll, insurance to cut fraud | Case study: UW $8 M overpayment shows risk |

A speedy, scripted offboarding process mitigates **insider threat** and supports evidence of due care.

### Role Definition and Transition

* Define new roles with **least privilege matrices** (permissions, groups, systems).  
* Use *Separation of Duties (SoD)* to avoid fraud (e.g., dev ≠ prod deploy).  
* During transfers/promotions, **remove old entitlements first** to curb privilege creep.

> Remember: RBAC changes should follow a formal **change-management workflow** to preserve audit trails.

### Account Maintenance

Ongoing tasks include:

* Password resets / MFA re-registration  
* Updates to **attribute data** (title, department) feeding role engines  
* Service account key rotation (90-day typical for high-privilege)  
* Certificate renewal before expiration

Administration scripts should be **idempotent** (repeatable with same result) and enforce policy baselines.

### Account Access Review

| Control | Focus | Frequency | Outcome |
|---------|-------|-----------|---------|
| **Inactive Account Scan** | No logon ≥ 30 days | Weekly | Auto-disable |
| **Privilege Review** | Administrator / root, service, system accounts | Monthly/quarterly | Remove excess rights |
| **Segregation Audit** | Conflicting roles (e.g., AP & AR) | Quarterly | SoD exception report |
| **Attestation** | Managers re-confirm team access | Annual | Compliance evidence |

*Issues Discovered*

| Term | Definition | Remedy |
|------|------------|--------|
| **Excessive privilege** | Rights > job needs | Revoke privileges |
| **Privilege creep** | Layered rights over time | Re-baseline role |

Automated identity-governance tools generate dashboards and evidence for ISO 27001, SOX, PCI DSS, etc.

## Summary

* The **identity & access provisioning life cycle** ensures that every account is *born secure, lives governed, and dies cleanly*.  
* **Provisioning/onboarding** grants correct initial access and educates the user.  
* **Deprovisioning/offboarding** withdraws all access and assets at exit—critical for insider-threat defense.  
* **Role definition/transition** aligns privileges with evolving business duties while enforcing least privilege and SoD.  
* **Account maintenance** keeps credentials, attributes, and systems in sync.  
* **Access reviews** detect and correct excessive privilege and privilege creep, providing audit assurance.  

Mastering this life cycle equips you to answer CISSP questions on RBAC, lifecycle management, and audit compliance with confidence ✅.


> **OWASP Session Management Cheat Sheet** is a must-know reference for best practices.



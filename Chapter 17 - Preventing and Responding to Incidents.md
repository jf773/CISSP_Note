# Chapter 17: Preventing and Responding to Incidents

- [Conducting Incident Management](#conducting-incident-management)
  - [Defining an Incident](#defining-an-incident)
  - [Incident Management Steps](#incident-management-steps)
- [Implementing Detection and Preventive Measures](#implementing-detection-and-preventive-measures)
  - [Basic Preventive Measures](#basic-preventive-measures)
  - [Understanding Attacks](#understanding-attacks)
  - [Intrusion Detection and Prevention Systems](#intrusion-detection-and-prevention-systems)
  - [Specific Preventive Measures](#specific-preventive-measures)
- [Logging and Monitoring](#logging-and-monitoring)
  - [Logging Techniques](#logging-techniques)
  - [The Role of Monitoring](#the-role-of-monitoring)
  - [Monitoring and Tuning Techniques](#monitoring-and-tuning-techniques)
  - [Log Management](#log-management)
  - [Egress Monitoring](#egress-monitoring)
- [Automating Incident Response](#automating-incident-response)
  - [Understanding SOAR](#understanding-soar)
  - [Machine Learning and AI Tools](#machine-learning-and-ai-tools)
  - [Threat Intelligence](#threat-intelligence)
  - [The Intersection of SOAR, Machine Learning, AI, and Threat Feeds](#the-intersection-of-soar-machine-learning-ai-and-threat-feeds)
- [Summary](#summary)


## Conducting Incident Management

### Defining an Incident
- **Core concept**: An **incident** is *any event that negatively affects* the confidentiality, integrity, or availability (CIA) of an organization’s assets.  
  - In CISSP context, *incident* **≡** *computer security incident*. 🌐  
- **Authoritative definitions**  
  - **RFC 2350**: “Any adverse event which compromises some aspect of computer or network security.”  
  - **NIST SP 800-61**: “A violation or imminent threat of violation of computer security policies, acceptable-use policies, or standard security practices.”  
- **Why wording matters**: The official definition is usually captured in a security policy or incident response plan; it dictates *scope*, *prioritization*, and *mandatory reporting*.

#### Event vs Incident (exam-critical distinction)
| Term | Description | Exam cues |
|------|-------------|-----------|
| **Event** | Observable change of state (e.g., log-off, link-up) that *may* be benign. | “Routine” noise; **not** automatically IR-worthy. |
| **Security Event** | Event with potential security relevance. | Raises *alert* but needs triage. |
| **Computer Security Incident** | Confirmed event that compromises CIA or violates policy. | Triggers full IR workflow. |

### Incident Management Steps
The CISSP exam emphasizes **seven** sequential steps (Figure 17-1). Remember: **_D R M R R R L_** – *Detection, Response, Mitigation, Reporting, Recovery, Remediation, Lessons Learned*.

| # | Step | Purpose | Key actions & tips |
|---|------|---------|--------------------|
| 1 | **Detection** 🔍 | Discover potential incidents. | IDS/IPS alerts, SOC monitoring, anti-malware pop-ups, user reports. *False positive triage* is part of this step. |
| 2 | **Response** 🚑 | Activate IR team (CSIRT/CIRT) and begin investigation. | Verify incident, escalate per playbook, preserve volatile evidence (⚡do **not** power off infected hosts). |
| 3 | **Mitigation** 🛑 | Contain/limit scope. | Quarantine hosts, disable interfaces, isolate subnets. Covert monitoring may continue to profile attacker. |
| 4 | **Reporting** 📝 | Notify stakeholders inside & outside the org. | Internal execs, regulators (PII laws), industry bodies (e.g., PCI-DSS), law enforcement (FBI, INTERPOL) as required. |
| 5 | **Recovery** ♻️ | Restore to normal ops. | Rebuild OS, restore data from backups, verify ACLs, re-patch, disable default accounts. |
| 6 | **Remediation** 🔄 | Eliminate root cause, prevent recurrence. | Root-cause analysis ➜ patches, code fixes, new controls, architectural changes. |
| 7 | **Lessons Learned** 🎓 | Institutionalize knowledge gained. | Post-mortem report, update runbooks/rules, improve detection thresholds, train staff. |

#### CISSP vs NIST SP 800-61 mapping
| CISSP 7-Step Model | NIST 4-Phase Model | Notes |
|--------------------|--------------------|-------|
| Detection | Detection & Analysis | NIST folds verification into same phase. |
| Response + Mitigation | Containment, Eradication & Recovery | CISSP splits containment (Mitigation) and restoration (Recovery). |
| Reporting | *Implicit* in every phase (esp. Detect & Recover) | Regulatory reporting spans multiple phases. |
| Recovery | Containment, Eradication & Recovery | |
| Remediation | Containment, Eradication & Recovery | Focus on root-cause fixes. |
| Lessons Learned | Post-Incident Activity | Continuous improvement feedback loop. |

> **Exam tip**: The CISSP will *refer explicitly* to the **seven-step model**; know the order and purpose of each step.

#### First-Responder Essentials
- **Triage skills** distinguish simple outages from bona fide incidents.  
- **Chain of custody** starts at first touch—document *who*, *what*, *when*, *where*, *how*.  
- Never launch **counterattacks** ⚔️—illegal and against policy.

#### Common Detection Technologies
| Technology | Typical alert | Strength | Weakness |
|------------|--------------|----------|-----------|
| IDS/IPS | Syslog/SIEM event | Real-time network visibility | False positives, needs tuning |
| EDR/XDR | Endpoint console pop-up | Granular host telemetry | Resource intensive |
| Log analytics (SIEM) | Correlated alert | Aggregates multi-source data | Rule quality critical |
| User reporting | Help-desk ticket | Context-rich, human intuition | Prone to errors/omissions |

> 🚩 **Remember**: Not every alert = incident. *Verify* before escalating to step 2.

#### Evidence Preservation Checklist
- Keep system **powered on** to capture RAM/volatile data.
- Use **write blockers** on disk imaging.  
- Generate cryptographic **hashes** (SHA-256) for integrity.  
- Store copies in **tamper-evident** containers with signed logs.

### Key Takeaways for the Exam ✅
- You must know **what constitutes an incident** and be able to differentiate it from an event.
- **Order and objective** of the seven steps are commonly tested memorization items.
- Understand **legal/regulatory reporting triggers** (PII breaches, PCI-DSS, GDPR).  
- Be ready to explain why **counterattacks are prohibited** and how to handle evidence properly.  

> 🌟 **Mnemonic**: **D**ogs **R**un **M**iles **R**eporting **R**ed **R**oses **L**ively  
> (Detection → Response → Mitigation → Reporting → Recovery → Remediation → Lessons Learned)

## Implementing Detection and Preventive Measures

### Basic Preventive Measures
A **preventive control** tries to stop an unwanted security event before it happens, while a **detection control** identifies it *after* it occurs.  
| Control Type | Typical Examples | Purpose | CISSP Hot-Button 🔥 |
|--------------|------------------|---------|--------------------|
| **Preventive** | 🔐 Locks, 🔒 firewalls, ✋ separation of duties, 🔁 job rotation, 🛡️ IDS/IPS (blocking mode), ✉️ security awareness training, ✨ encryption, 👤 biometrics | *Thwart* unauthorized activity | Know that many “preventive” controls (e.g., **IPS**) can also generate **detection** alerts |
| **Detection** | 🚨 Motion sensors, 🎦 CCTV review, 📜 audit logs, 🪤 honeypots, 🧑‍💼 supervision, 📝 violation reports, IDS/IPS (alert mode) | *Discover* an event after it occurs | Mandatory-vacation audits and honeynets are classic **detection** mechanisms |

Foundational steps every organization should take:

1. **Patch management**  
   - Apply vendor patches promptly; ties directly into *risk management* (Domain 2).  
2. **Disable unneeded services/protocols**  
   - Reduces *attack surface* (fewer ports, fewer daemons to exploit) 🛠️  
3. **Deploy IDS/IPS**  
   - Detect *and* optionally block malicious traffic; must be tuned to minimize false positives.  
4. **Maintain up-to-date anti-malware**  
   - Signature + behavior analysis; pair with application whitelisting for extra coverage.  
5. **Use host & network firewalls**  
   - Default-deny rules, segmented zones; log & alert on policy violations.  
6. **Follow configuration/change-management processes**  
   - Baselines, version control, peer review, roll-back plans.  
7. **Continuous user education** 📚  
   - Phishing simulation, social-engineering drills—still one of the best ROI controls.  

> 💡 **Exam tip:** The CISSP often asks for *the single most effective* first step; keeping systems **patched** usually tops the list.

---

### Understanding Attacks
Security pros must recognize **how** adversaries operate to pick the right controls.

#### Botnets 🤖
- **Definition:** Networks of compromised hosts (**bots/zombies**) remotely controlled by a **bot herder** via C2 servers.  
- **Uses:** DDoS, spam, credential stuffing, renting out for crime-as-a-service.  
- **Defense-in-Depth:** Anti-malware, patched OS/apps, egress filtering, DNS sinkholing, user-awareness training.

#### Denial-of-Service (DoS / DDoS / DRDoS)
| Variant | Mechanism | Key CISSP Points | Common Mitigations |
|---------|-----------|------------------|--------------------|
| **DoS** | Single attacker floods or exploits a vuln | Easy to trace if not **spoofed** | Rate limiting, resource tuning |
| **DDoS** | *Many* sources (often botnet) overwhelm target | Harder to block IPs; sheer volume | Cloud scrubbing, anycast CDN |
| **DRDoS** | Uses *reflectors* to amplify traffic back to victim (e.g., DNS, NTP) | “Indirect” flood—spoofed victim IP | Disable open resolvers, BCP 38 egress-filtering |

##### SYN Flood 🌊
- **Abuse:** Leaves TCP handshakes half-open, exhausts queue.  
- **Countermeasures:** SYN cookies, shorter SYN-ACK timeout, state-tracking firewalls/IPS.

##### TCP Reset Attack
- Sends forged **RST** to kill persistent sessions (e.g., BGP, long-lived DB connections).  
- Mitigate with encrypted tunnels (TLS, IPsec) and sequence-number validation.

##### Smurf / Fraggle 🐟
| Attack | Protocol | Amplification Method | Modern Relevance |
|--------|----------|----------------------|------------------|
| Smurf | ICMP (ping) | Directed broadcast of **echo-request** | Rare if RFC 2644 filtering enabled |
| Fraggle | UDP ports 7/19 | Broadcast echo/chargen | Blocked if UDP broadcast is disabled |

##### Ping Flood
- Massive ICMP echo requests (common as botnet DDoS).  
- Solution: Rate-limit ICMP, anomaly-based IDS, temporary drop ICMP echo.

##### Legacy DoS Attacks 🕰️ *Know by name for exam*
- **Ping of Death** (oversized ICMP)  
- **Teardrop** (overlapping IP fragments)  
- **LAND / Banana** (spoofed SYN from victim to itself)  
> These highlight why **input validation & patching** matter.

---

#### Zero-Day Exploit 🚨
- **Classic meaning:** Vulnerability known **only to attacker**; no patch exists.  
- **Other usages:**  
  1. Vendor aware but patch not released.  
  2. Patch released but org hasn’t applied it (sometimes called “Exploit Wednesday”).  
- **Protection:** Minimize services, application whitelisting, network segmentation, heuristic IDS/IPS, honeypots for intel.

#### Man-in-the-Middle (On-Path)
- **Goal:** Intercept/alter traffic between two endpoints.  
- **Techniques:** ARP spoofing, rogue Wi-Fi AP, SSL/TLS stripping, malicious proxies.  
- **Controls:** End-to-end encryption (TLS 1.3 with cert pinning), secure DNS (DNSSEC, DoH), VPN tunnels, mutual authentication.

| Attack Type | Passive vs Active | Detection Difficulty | Typical Control |
|-------------|------------------|----------------------|-----------------|
| Sniffing | Passive | High | Encryption-in-transit |
| **MiTM** | *Active* (forwards & alters) | Moderate | Cert pinning, VPN, HSTS |
| Session Hijack | Active (takes over cookies/ID) | Moderate | Secure cookies, MFA, rekeying |

#### Sabotage (Insider Threat) 🛠️
- **Motivation:** Disgruntlement, revenge, coercion.  
- **Triggers:** Pending termination, perceived injustice, ideological conflict.  
- **Safeguards:**  
  - Immediate privilege revocation at dismissal 🔒  
  - Least-privilege & segregation of duties  
  - Intensive log monitoring & UEBA (user/entity behavior analytics)  
  - Culture of recognition and open communication to reduce grievances

### Quick Reference ✏️
| Attack / Issue | Primary CIA Impact | Best First-Line Control |
|----------------|-------------------|-------------------------|
| Botnet join | **C**/*I*/A | Updated anti-malware, user training |
| SYN flood | *A* | SYN cookies, IDS/IPS |
| Zero-day | C/I/A | Defense-in-depth, patch agility |
| MiTM | **C** & **I** | Strong encryption, cert pinning |
| Insider sabotage | C/I/**A** | Access disablement, monitoring |

> 🎯 **Remember for CISSP:** The exam often asks which *single* measure best mitigates an attack. Think **patches** for known vulns, **encryption** for MiTM, **segmentation** for botnet containment, and **rate limiting** or **cloud DDoS services** for volumetric floods.

## Intrusion Detection and Prevention Systems

### Concept and Terminology
- **Intrusion Detection System (IDS)** 🕵️‍♂️: Monitors events/logs **in real time** to spot abnormal or malicious activity.  
- **Intrusion Prevention System (IPS)** 🛡️: Everything an IDS does **plus** the ability to block or stop the traffic (must be *inline*).  
- **IDPS**: Umbrella term used by NIST SP 800-94 to cover both.  
- **Key goal**: *Timely & accurate* detection **and** (optionally) interruption of intrusions as part of a **defense-in-depth** architecture—never a replacement for firewalls.

### Detection Approaches
| Approach | Also called | How it works | Strengths | Weaknesses |
|----------|-------------|--------------|-----------|------------|
| **Knowledge-based** 🔍 | Signature / pattern-matching | Compares events to a DB of known attack patterns | Low false-positive rate; quick to update | No defense vs unknown/modified attacks (high false-negative) |
| **Behavior-based** 📈 | Anomaly / statistical / heuristic | Builds a *baseline* of “normal” behaviour, flags deviations | Detects *new or obfuscated* attacks; learns over time | High false-positive rate; baseline drift; tuning required |

> 💡 **Exam tip**: Signature = fewer false positives, more false negatives; Behavior = opposite.

#### False/True Matrix  
- **True Positive**: real attack & detected  
- **False Positive**: no attack, alert triggered (nuisance)  
- **False Negative**: real attack, *missed* (dangerous)  
- **True Negative**: no attack, no alert  

### Response Modes
| Mode | What it does | Example actions |
|------|--------------|-----------------|
| **Passive** | Log + notify only | Email/SMS to SOC, SIEM dashboard |
| **Active** | Modify environment | Auto-edit ACL, TCP RST, quarantine host |

> If placed inline and actively blocking, the device is functionally an **IPS/NIPS**.

### Deployment Models
| Type | Monitors | Pros | Cons |
|------|----------|------|------|
| **HIDS** 🖥️ | Single host (logs, processes) | Detects local exploits; deep visibility | Resource-heavy; cannot see network; easier to tamper |
| **NIDS** 🌐 | Network traffic via taps/SPAN | One sensor covers many hosts; stealthy | Encrypted traffic blind spot; cannot confirm host compromise |
| **Application-based IDS** | Specific app-to-app flows | Granular protocol awareness | Narrow scope; complexity |

### Handling Encrypted Traffic
- **TLS decryptor/SSL off-load appliance** decrypts HTTPS, feeds clear traffic to IDPS, then re-encrypts outbound stream.  
- Limitation: Host-encrypted payloads (pre-TLS) or APT custom crypto remain opaque.

### Intrusion Prevention System (IPS) Highlights
- **Inline** with the data path—can drop packets before target sees them.  
- Often implemented as a **next-generation firewall (NGFW)** or combined UTM appliance.  
- Trend: Convert legacy NIDS → NIPS by relocating sensors inline.

---

## Specific Preventive Measures

### Honeypots & Honeynets 🍯
| Term | Definition | Purpose |
|------|------------|---------|
| **Honeypot** | Single decoy host (often VM) with deliberate vulns | Divert, slow, and study attackers; gather intel on zero-days |
| **Honeynet** | Two + interconnected honeypots | Simulate fuller environment, richer telemetry |

- Use **pseudo-flaws** to entice attackers; legal if *enticement* not *entrapment*.  
- Snapshot VMs for quick revert; monitor closely to avoid *VM escape*.

### Warning Banners 📝
- Digital “no-trespassing” signs: notify users that activity is monitored, binding them to policy.  
- Strengthens legal standing for prosecution and privacy notice.

### Anti-malware (Endpoint Protection)
- Signature + heuristic engines; update multiple times **per day**.  
- **Layered strategy**: Secure email gateway ✉️, NGFW/UTM at perimeter 🌐, endpoint AV/EDR 🖥️.  
- One product per host (avoid engine conflicts); enforce **least privilege**; continuous user awareness training.

### Allow (Whitelist) vs Deny (Blacklist) Lists
| List type | What runs | Use-case | Example |
|-----------|-----------|----------|---------|
| **Allow list** ✅ | *Only* approved hashes/paths | High-security hosts, kiosks, iOS model | Hash-based AppLocker rules |
| **Deny/Block list** 🚫 | Everything except banned items | Quick way to block known bad apps | Add games to company block list |

> A host uses **either** an allow list **or** a deny list, never both simultaneously.

### Firewalls 🧱
| Generation | Core Capability | Typical Layer | Extra Features |
|------------|-----------------|---------------|----------------|
| 1st (Packet filter) | Static ACL (IP, port, protocol) | L3/L4 | - |
| 2nd (Application / Circuit) | Inspect at application gateway / session | L5/L7 | Proxy functions |
| 3rd (Stateful inspection) | Tracks connection *state* | L3–L7 | Dynamic rules |
| **NGFW / UTM** | Combines stateful + IDPS + malware filter + SSL decrypt | L3–L7 | App-ID, user-ID, Sandboxing |

- **Edge recommendations**:  
  - Block *directed broadcasts* 🚫  
  - Drop *private IP source* on WAN interface 🌐  
  - Rate-limit or block **ICMP echo** if needed against ping floods  

- Specialized firewalls: **WAF** protects web apps (SQLi, XSS); **NGFW** adds user/app awareness.

### Sandboxing 🧪
- VM/Container isolation to run **untrusted** code safely.  
- Used by AV vendors, developers, and browser engines; blocks lateral infection if code is malicious.

### Third-Party Security Services
- Outsource SOC, penetration testing, or DDoS scrubbing to specialized providers.  
- Must ensure providers meet regulatory obligations (e.g., **PCI DSS**)—outsourcing **does not outsource accountability**.

### Quick-Look Tables

#### IDS vs IPS
| Feature | IDS | IPS |
|---------|-----|-----|
| Placement | Out-of-band | Inline |
| Latency impact | None | Adds processing delay |
| Can block traffic | No (except active after-the-fact) | Yes (real time) |
| Primary use | Alerting/forensics | Prevention + alerting |

#### Preventive Controls Cheat Sheet
| Control | Attack Mitigated (Primary) | Exam Key Point |
|---------|---------------------------|----------------|
| Honeypot | Zero-day reconnaissance | Enticement legal, entrapment not |
| Warning banner | Insider threat evidence | Establishes monitoring consent |
| Allow list | Unauthorized/malware apps | Blocks *everything* not explicitly allowed |
| NGFW with SSL decrypt | Encrypted C2, malware | Inline decryption → inspection |
| Sandboxing | Unknown executables | Contain code, observe safely |

> 🔑 **Remember for CISSP**: When multiple answers seem correct, pick the one addressing the *root cause* at the *earliest stage* (e.g., allow lists > AV signatures for preventing rogue apps).

## Logging and Monitoring

### Logging Techniques
- **Purpose**: Capture *who*, *what*, *when*, *where*, and sometimes *how* an event occurred to support accountability, forensics, and compliance. 📝  
- **Logging vs Auditing**  
  - *Logging* = recording events.  
  - *Auditing* = examining those records (see Chapter 15).  

#### Common Log Types
| Log Type | Typical Contents | Why It Matters for CISSP |
|----------|-----------------|---------------------------|
| **Security** | File/print access, object deletion, privileged actions | Proves user accountability and supports IR |
| **System** | Boots/shutdowns, service start/stop, driver errors | Detects tampering (e.g., disabled AV service) |
| **Application** | App-specific events (e.g., DB table query) | Shows misuse of business apps |
| **Firewall** | Allowed/blocked flows, src/dst IP:port | Validates rule set; traces attack paths |
| **Proxy/Web** | URL visited, user, bandwidth | Enforces AUP; detects C2 beacons 🌐 |
| **Change Mgmt** | Requested, approved, implemented changes | Supports rollback, DR, compliance evidence |

> **Exam tip**: *Privileged-account activity* is always high-value log data.

#### Protecting Log Data
- **Centralize** to SIEM or log server (immutable copies).  
- Restrict *write* access; set logs **read-only** where feasible.  
- Define **retention & destruction** schedules to balance legal/regulatory needs vs storage cost.  
- Synchronize timestamps via **NTP**; consistency is critical for event correlation.  
- Follow **FIPS 200** audit minimums (trace user actions; retain records for monitoring/investigation).

### The Role of Monitoring
- **Audit Trails**  
  - Chronological record of system and user activity; support *reconstructing* incidents.  
  - Passive deterrent (like CCTV) but essential evidence for prosecution. ⚖️  

| Benefit Area | Key Points | CISSP Angle |
|--------------|-----------|-------------|
| **Accountability** | Links actions to authenticated IDs; promotes policy compliance | Needed for due care/ diligence |
| **Investigations** | Rebuild timeline, prove or refute culpability; integrate with IR playbooks | Chain-of-custody, legal admissibility |
| **Problem Identification** | Detect hardware faults, performance issues, software bugs | Distinguish attack vs malfunction |
| **Regulatory Compliance** | SOX, HIPAA, GDPR demand specific monitoring practices | Demonstrate control effectiveness |

- **Monitoring Best Practices**  
  - Use **SIEM** for real-time correlation and alerting.  
  - Tune alerts to minimize noise (false positives).  
  - Regularly review dashboards and reports—*logging without monitoring is futile*.  
  - Train staff: personnel who know they are monitored are less likely to violate policy. 🙂  

> 🔑 **Remember for CISSP**: Effective logging + vigilant monitoring = the backbone of detection, accountability, and forensic readiness.

### Monitoring and Tuning Techniques

> Monitoring answers *“What’s happening right now?”*  
> Tuning answers *“Are we getting the right signals with minimal noise?”*

| Activity | Goal | Key CISSP Points |
|----------|------|------------------|
| **Continuous monitoring** 🛰️ | Real-time visibility of events across hosts, network, cloud | Drives rapid detection; often mandated by frameworks (e.g., NIST RMF “CM” family) |
| **Tuning** ⚙️ | Reduce false positives/negatives; align alerts with risk | Adjust IDS/IPS signatures, SIEM rules, clipping levels; iterative process |
| **Log analysis** | Mine logs for trends/anomalies (manual or automated) | Essential in IR post-mortem; supports baselining |
| **SIEM** | Centralize, correlate, retain, and alert | Features: agents, correlation engine, rule-based & ML analytics, dashboards |
| **Syslog (RFC 5424)** | Industry-standard event transport; UDP/TCP 514 | Extensions (syslog-ng, Rsyslog) ingest multi-platform logs into SIEM |
| **Sampling** | Stat. or non-stat. data reduction for large log sets | Statistical = margin-of-error; Non-stat. = clipping thresholds |
| **Clipping levels** | Alert only after N events/time (e.g., 5 bad logons/30 min) | Minimizes alert fatigue; part of tuning |
| **Other tools** | CCTV, keyloggers (with notice!), flow monitoring | Complements log-centric view; supports physical/insider controls |

> 💡 **Exam tip**: A SIEM with proper *correlation* + *tuning* is the most powerful way to convert raw logs into actionable intelligence.

---

### Log Management

The *log management life-cycle*:

| Phase | Tasks | Best-practice Highlights |
|-------|-------|--------------------------|
| **Collection** | Generate & forward events (agents, Syslog, Windows Event Forwarding) | Enable on critical systems/privileged accounts first |
| **Transmission** | Secure channel to SIEM (TLS, VPN) | Prevent tampering/sniffing |
| **Storage** | Central SIEM DB, WORM media, or secure file share | Write-once/append-only; disk encryption |
| **Retention** | Keep per policy/regulation (e.g., SOX = 7 yrs, PCI = 1 yr) | Over-retention ↑ e-discovery cost |
| **Protection** | Permission hardening, hashes, backups, physical security | Maintain chain-of-custody for legal use |
| **Disposition** | Rollover/circular logs or archive & purge | Prevent disk-fill DoS; follow data-destruction policy |

Key mechanics:

* **Rollover logging** (circular) - overwrite oldest events once max size hit.  
* **Archival logging** - auto-save full log to file, start new log (risk: drive fill).  
* **SIEM aggregation** allows deletion on sources once ingested + verified.  
* **Time-sync** via internal NTP rooted to trusted public source → consistent forensics.

### Egress Monitoring

**Definition**: Inspect outbound traffic for *unauthorised* or *sensitive* data transfers—crucial for spotting data exfiltration 🚨.

| Threat Vector | Monitoring/Control | How It Works |
|---------------|--------------------|--------------|
| **DLP** | Content & contextual analysis of outbound SMTP, HTTP/S, FTP | Regex, fingerprints, watermarks; block/quarantine |
| **Steganography** | Hash comparison of baseline vs outbound media; forensic tools | Mismatch hints hidden payload; escalate for deep analysis |
| **Watermarked data** | Detect corporate watermark in clear files | SIEM/DLP rule triggers alert/block |
| **Encrypted exfil** | Monitor *volume*, *destination*, *anomalous host* using flow analytics | Flag unusual large TLS uploads; correlation with user context |
| **Policy-based firewall/NGFW** | Allow only sanctioned protocols/ports; TLS inspection | Stops shadow-IT tunnels, unauthorized VPNs |

Implementation tips:

1. **Mirror outbound links** to IDS/IPS or NGFW with **SSL decrypt** when policy permits.  
2. **Baseline normal egress** (GB/day, destinations) → alert on deviations 📈.  
3. Combine **DLP** with **endpoint controls** (disable USB mass-storage, clipboard restrictions).  
4. Align egress rules with *data classification* schema defined in Domain 2.

> 🔑 **Remember for CISSP**: Outbound monitoring is as important as inbound filtering—data loss hurts confidentiality, brand, and compliance.

## Automating Incident Response

### Understanding SOAR
Security **O**rchestration, **A**utomation, and **R**esponse (SOAR) platforms stitch together alerts, data, and workflows so that repetitive response actions happen **without human lag**.

| Concept | What It Means | CISSP Nuggets |
|---------|---------------|---------------|
| **Playbook** | Human-readable checklist that *defines* verification & response steps | Serves as backup if automation fails |
| **Runbook** | Machine-executable workflow implementing a playbook | Written in low-/no-code or YAML; triggered by SIEM/IDPS |
| **Orchestration** | Integrate many tools (SIEM, EDR, ticketing, firewalls) via APIs | Reduces swivel-chair fatigue |
| **Automation** | Pre-approved actions (e.g., isolate host, block IP, reset PW) | Cuts MTTR (Mean Time To Respond) |
| **Response** | Evidence collection, notifications, containment, remediation | Must preserve chain of custody 🔒 |

> 💡 **Exam tip**: SOAR ≠ SIEM. SIEM *detects & correlates*; SOAR *decides & acts*.

### Machine Learning and AI Tools
| Term | Simple Definition | Security Use-Case Examples |
|------|-------------------|----------------------------|
| **Machine Learning (ML)** | System improves using *training data* + feedback | Baseline-driven anomaly IDS; malware family classifier |
| **Artificial Intelligence (AI)** | Broader field: systems that infer, reason, and adapt (ML subset) | Autonomous SOC assistants, natural-language triage bots |

Core differences:

1. **Starting knowledge** – ML starts with rules/data; AI may learn rules itself.  
2. **Adaptation loop** – Both rely on feedback (true/false positives) to refine models.  
3. **CISSP viewpoint** – Know that vendors’ “AI” claims might simply be advanced ML with human-curated rules.

### Threat Intelligence
Gathering, enriching, and operationalising **current attacker TTPs**.

| Layer | Description | Typical Sources |
|-------|-------------|-----------------|
| **Strategic** | High-level trends, nation-state motives | Gov’t CERT advisories, ISAC briefings |
| **Operational** | Campaign & actor profiles, kill-chain insights | Dark-web monitoring, APT reports |
| **Technical** | Domains, IPs, hashes, YARA rules | Commercial TI feeds, VirusTotal |
| **Tactical** | Real-time indicators for controls (blocklists) | STIX/TAXII feeds into firewalls/IDPS |

Frameworks to know:

- **Lockheed-Martin Cyber Kill Chain** – seven sequential phases (Recon → Actions).  
- **MITRE ATT&CK** – matrix of tactics (Privilege Escalation, Lateral Movement…) with techniques & mitigations.

### The Intersection of SOAR, Machine Learning, AI, and Threat Feeds
- **Threat feed ➜ SIEM correlation ➜ SOAR runbook**: Malicious IP appears in feed → SIEM match → SOAR auto-blocks firewall rule & opens ticket.  
- **ML-enhanced SOAR**: Model ranks alert severity; runbook branches accordingly (high = auto-isolate, low = queue for analyst).  
- **AI assistance**: Chat-style agent summarizes incident timeline or drafts post-incident report ✍️.

> ⚠️ **Risk**: Over-automation can act on *false positives* ➜ always build manual-approval gates for high-impact actions.

## Summary
- **SOAR** turns documented **playbooks** into automated **runbooks**, orchestrating disparate tools to slash response time.  
- **Machine Learning** fine-tunes detection baselines; **AI** aspires to synthesize rules and context on its own.  
- **Threat Intelligence** (strategic → tactical) supplies actionable indicators; integrating feeds into SOAR keeps controls current.  
- When combined, **SOAR + ML/AI + TI** create a feedback-rich, self-updating defense loop—yet still require human oversight for corner cases and legal accountability. ✅


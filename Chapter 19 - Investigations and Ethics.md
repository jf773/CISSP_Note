# Chapter 19: Investigations and Ethics

- [Investigations](#investigations)
  - [Investigation Types](#investigation-types)
  - [Evidence](#evidence)
  - [Investigation Process](#investigation-process)
- [Major Categories of Computer Crime](#major-categories-of-computer-crime)
  - [Military and Intelligence Attacks](#military-and-intelligence-attacks)
  - [Business Attacks](#business-attacks)
  - [Financial Attacks](#financial-attacks)
  - [Terrorist Attacks](#terrorist-attacks)
  - [Grudge Attacks](#grudge-attacks)
  - [Thrill Attacks](#thrill-attacks)
  - [Hacktivists](#hacktivists)
- [Ethics](#ethics)
  - [Organizational Code of Ethics](#organizational-code-of-ethics)
  - [ISC2 Code of Professional Ethics](#isc2-code-of-professional-ethics)
  - [Ethics and the Internet](#ethics-and-the-internet)
- [Summary](#summary)

## Investigations  
High-level, structured inquiries that determine **what happened, how it happened, who is responsible, and what evidence supports the findings**. Security professionals must balance operational needs with legal, regulatory, and ethical mandates.  

**🎯 Investigation Objectives**
- **Contain & eradicate** incidents while preserving evidence.  
- **Attribute** actions to individuals or systems.  
- **Support enforcement** (administrative, civil, criminal, or regulatory).  
- **Strengthen controls** to prevent recurrence.

### Investigation Types  
| Type | Authority / Lead | Proof Standard | Typical Venue | Key Points |
|------|------------------|----------------|---------------|------------|
| **Administrative / Operational** | Internal mgmt / HR / IT | Varies by policy; often *reasonable belief* | Internal disciplinary / troubleshooting | 🛠️ Fast, informal; may transition into other types. |
| **Criminal** | Law-enforcement (e.g., FBI Cyber Division) | **Beyond a reasonable doubt** (highest) | Criminal court | Must follow strict evidence rules (chain of custody, warrants, etc.). |
| **Civil** | Private parties & counsel | **Preponderance of the evidence** (≥ 51 %) | Civil court (lawsuits) | Less stringent than criminal; often monetary remedy. |
| **Regulatory** | Gov. agencies (e.g., SEC, FTC) | Depends on statute; often *clear & convincing* | Administrative court / hearings | Non-compliance may trigger fines, orders, or revocation. |
| **Industry-Standard / Contractual** | Independent assessor (e.g., PCI QSA) | Contract terms | Contract arbitration / penalties | Non-legal but binding; similar rigor to regulatory. |

> 🔑 **Tip:** Know which investigation type applies **before** evidence collection begins—the admissibility bar differs.

#### Electronic Discovery (eDiscovery) & EDRM  
- **EDRM 9-step model**: Information Governance → Identification → Preservation → Collection → Processing → Review → Analysis → Production → Presentation.  
- **Goal**: Efficiently locate, protect, and deliver electronic data responsive to legal demands.

### Evidence  
*Proof* presented to establish facts in dispute. For CISSP, recall the **three admissibility criteria** and **four primary evidence categories**.

#### Admissibility Requirements (all must be met)  
1. **Relevance** – tends to prove/disprove a fact.  
2. **Materiality** – fact is germane to the case.  
3. **Competency** – legally obtained (no illegal search, no coercion).

#### Evidence Categories  
| Type | Definition | Extra Rules / Notes | Example |
|------|------------|---------------------|---------|
| **Real / Physical** | Tangible objects that can be brought to court. | Often requires chain-of-custody. | Seized hard drive, USB, laptop. |
| **Documentary** | Written/digital records. | Must satisfy **Best Evidence** & **Parol Evidence** rules. | Syslog files, policies, contracts. |
| **Testimonial** | Oral or written statements by witnesses. | Subject to **oath**, **personal knowledge**, and **hearsay** restrictions. | Admin’s sworn affidavit explaining log authenticity. |
| **Demonstrative** | Illustrative aids that clarify testimony. | Admitted if they help the jury understand. | Network attack diagram, timeline graphic. |

#### Best Evidence Rule  
Original documents preferred; copies allowed only under defined exceptions (e.g., certified copies, loss not due to bad faith).

#### Hearsay & Business Records Exception  
Computer-generated logs are usually admissible if:  
- Created **at/near** time of event  
- **Routine business practice**  
- Authenticated by custodian or qualified witness

#### Chain of Custody 🧾  
Unbroken, documented record of **who**, **what**, **when**, **where**, **why** for every evidence hand-off. Label must include:  
- Description  
- Date & time collected  
- Exact location  
- Collector’s name  
- Circumstances of acquisition  

> 🔒 **Preserve the original**; examine only verified images/clones.

#### Digital Forensics Principles (IOCE)  
1. Actions must **not alter evidence**.  
2. Only **competent** personnel access originals.  
3. **Document** all actions.  
4. Individual assumes responsibility while evidence in their control.  
5. Agency enforces compliance with these principles.

#### 🛡️ Preserving the Original

1. **Create a forensic image** (bit-for-bit copy) of the device or media.  
2. **Seal the original** in an evidence bag; store in a controlled locker.  
3. **Hash (e.g., SHA-256) the source and the image** → ensure they match.  
4. Perform all examinations on **verified copies** only.  
5. Document every action in the **chain of custody**.

#### Media Analysis

| Step | Key Actions | Purpose / Notes |
|------|-------------|-----------------|
| Isolation | Power off system; remove drive | Prevent live-system writes |
| Write-blocking | Attach via hardware write blocker | Physically prevents alteration |
| Imaging & Hashing | Create forensic image → hash source & image | Confirms integrity |
| Analysis | Recover deleted files, inspect unallocated space, analyze encrypted media | Use trusted forensic suites |

#### In-Memory Analysis

- Capture a **memory dump** from the live system (trusted tool + forensically prepared USB).  
- Immediately compute and record a **hash** of the dump file.  
- Preserve the original dump; analyze only its copies.  
- Focus areas: running processes, loaded drivers, crypto keys, injected code.

#### Network Analysis

Data sources to correlate:

* IDS/IPS logs  
* NetFlow / sFlow records  
* On-demand packet captures  
* Firewall / WAF logs  

**Collection tips**

- Mirror traffic via **SPAN port** or **network tap** (non-intrusive).  
- Store captures on write-protected media; hash files; maintain chain of custody.  
- Reconstruct timelines to reveal attacker path, exfil routes, C2 channels.

#### Software Analysis

- **Static review**: scan source code/binaries for backdoors, logic bombs, or malware signatures.  
- **Log analysis**: parse app / DB logs for SQLi, privilege escalations, unusual API calls.  
- **Hash validation**: compare file hashes against the **NIST NSRL** (≈ 130 M known good hashes) to spot tampered or rogue files.

#### Hardware / Embedded Device Analysis

Target devices: PCs, smartphones, IoT/OT controllers, vehicle ECUs, alarm systems.  
Requires **specialized expertise** in proprietary OSs, storage, and memory layouts. Often combines media + software techniques; organizations may engage external specialists.

#### Locard’s Exchange Principle 🔍

> **“Every contact leaves a trace.”**

*Physical* forensics meets *cyber* forensics:

| Attack Stage | Likely Traces |
|--------------|--------------|
| Attacker’s device | Tool artifacts, login history, physical fingerprints |
| Intermediate network | Router/firewall/IDS logs, packet captures |
| Target web server | Access logs, WAF alerts, modified files |
| Database server | Query logs, changed records |

Remember: by mapping each interaction point, investigators stitch together the full intrusion narrative.

### Investigation Process  
A repeatable workflow ensuring due diligence, legality, and integrity.

#### 1️⃣ Preparation  
- **Policy & IR plan** define when to trigger an investigation.  
- Assemble multidisciplinary **investigation team** (IR, legal, forensic, HR, exec).  
- Draft **scope/charter** & **rules of engagement** (e.g., when to involve LE, authority boundaries).

#### 2️⃣ Evidence Gathering  
| Mechanism | Use Case | Risk / Caveat |
|-----------|----------|---------------|
| **Voluntary consent** | Internal assets or cooperative party | May alert suspect; ensure proper documentation. |
| **Subpoena / Court order** | Compel third-party data (ISP, cloud) | Notice period can allow tampering. |
| **Plain-view seizure** | Evidence visible during lawful presence | Must have **probable cause**. |
| **Search warrant** | Secretive collection; high legal protection | Requires sworn probable cause & specificity. |
| **Exigent circumstances** | Imminent destruction of evidence or danger | Limited scope; justify urgency. |
| **Employment consent on hire** | Org-owned assets | Include in acceptable-use policy. |

> 🛑 **Never hack back** – illegal in most jurisdictions.

#### 3️⃣ Conducting the Investigation  
1. **Isolate** affected systems; create **forensic images** using write-blockers.  
2. **Hash** originals & images (e.g., SHA-256) for integrity.  
3. Perform **media, memory, network, software, and hardware analysis** on copies.  
4. **Correlate** data (logs, packet captures, timelines) applying **Locard’s Exchange Principle** (“every contact leaves a trace”).  
5. Maintain **detailed notes** – who did what, when, with which tools.

#### 4️⃣ Interviews & Interrogations  
- Plan with a **question checklist**; adapt dynamically.  
- Distinguish **interview** (fact-finding) vs **interrogation** (suspect questioning).  
- Follow legal rights (e.g., counsel, Miranda in US).  
- Use trained personnel; improper methods may taint evidence.

#### 5️⃣ Data Integrity & Retention  
- Implement **remote centralized logging** & **digital signatures**.  
- Align log retention with regulatory (e.g., SOX, HIPAA) & investigative needs.  
- Secure logs against alteration (WORM storage, SIEM with checksum).

#### 6️⃣ Reporting & Documentation 📝  
- **Final report**: objectives, timeline, tools, evidence list, findings, and recommended actions.  
- Use **standard templates & checklists** to ensure completeness.  
- Store securely; follow org. classification & retention policy.  
- Establish **single point of contact** for law enforcement (consider InfraGard memberships).  

#### Quick-Reference Cheat Sheet ⚡  
| Concept | Key Number / Phrase | Why It Matters |
|---------|--------------------|----------------|
| Admissibility | **Relevant + Material + Competent** | Judge’s gate for evidence. |
| Criminal Proof Standard | **Beyond a reasonable doubt** | Highest bar; plan collection accordingly. |
| Civil Proof Standard | **Preponderance (> 50 %)** | Easier to satisfy than criminal. |
| Chain of Custody | **Unbroken documentation** | Proves evidence unchanged. |
| EDRM Steps | **9** (IG → ID → Pr → Co → Proc → Rev → An → Prod → Pres) | Guides eDiscovery lifecycle. |
| Locard Principle | “**Every contact leaves a trace**” | Encourages exhaustive source search. |

> ✅ **Exam Hint:** Memorize evidence categories & rules (best evidence, hearsay exceptions) and match investigation types to proof standards.

## Major Categories of Computer Crime

Understanding **why** attackers strike is just as important as knowing **how** they break in.  The CISSP exam expects you to distinguish major crime categories, the motives behind them, and the unique traces they leave behind.  

#### 🗺️ Quick Comparison Table

| Category | Primary Motivation | Typical Targets | Typical Skill / Resources | Common Impact / Evidence |
|----------|-------------------|-----------------|--------------------------|--------------------------|
| Military & Intelligence | Strategic advantage, national security | Defense, law-enforcement, R&D labs | Highly skilled, nation-state backed (APT) | Silent exfiltration; minimal logs |
| Business | Competitive gain, sabotage | Competitors, supply chain | Skilled insiders or contractors | IP theft, ransomware, reputation loss |
| Financial | Direct monetary gain | Banks, e-commerce, end-users | Varies (low-skill fraud ➜ organized crime) | Fraudulent Tx, card dumps, ransom notes |
| Terrorist | Fear, disruption | Critical infrastructure, public services | Moderate–high; may combine physical & cyber | SCADA/ICS outages, propaganda |
| Grudge | Revenge | Former employer, individuals | Insider familiarity | Data wiping, defamatory leaks |
| Thrill | Entertainment, notoriety | Any vulnerable host | Low (script-kiddies) | Defacements, DoS noise, brag posts |
| Hacktivist | Ideological protest | Gov’t, corporations | Crowdsourced, tool-assisted | DDoS, data dumps, social-media leaks |

### Military and Intelligence Attacks

#### Overview  
*Goal:* 🎯 Obtain restricted or classified data that can alter military plans or diplomatic leverage.

#### Attack Goals  
- Order-of-battle, troop readiness, or classified R&D  
- LE investigation details (to compromise cases)  
- Insert long-term footholds for future ops

#### Common Tactics  
- **APT campaigns** (spear-phishing → privilege escalation → covert C2)  
- Zero-day exploits against hardened perimeters  
- Supply-chain compromises (esp. defense contractors)

#### Evidence Characteristics  
- Extremely low noise; professionally scrubbed logs  
- Encrypted outbound tunnels on non-standard ports  
- Overlapping time-zones/patterns tied to sponsor nation

#### Defensive Focus 🛡️  
- Formal data classification & segmentation  
- Strict need-to-know + MFA + continuous monitoring  
- Threat hunting for **APT TTPs** (MITRE ATT&CK mapping)

### Business Attacks

#### Overview  
*Goal:* 💼 Gain competitive edge or sabotage a rival’s operations / reputation.

#### Sub-Motivations  
- **Industrial espionage** – steal IP, source code, formulas  
- **Sabotage** – disrupt manufacturing, supply chain, or brand image  
- **Ransomware** – deny availability, extort payment

#### Common Tactics  
- Insider planting USB, abusing cloud storage  
- BEC (Business E-mail Compromise) for wire-fraud  
- Ransomware-as-a-Service targeting backups

#### Evidence & Indicators  
- Unusual file access by privileged accounts after hours  
- Lateral movement toward file shares / code repos  
- Outbound traffic to paste sites or criminal marketplaces

#### Defensive Focus  
- Data Loss Prevention (DLP) & CASB rules  
- Insider risk programs; off-boarding checklists  
- Immutable backups & tabletop ransom drills

### Financial Attacks

#### Overview  
*Goal:* 💰 Direct profit—steal, divert, or extort money/services.

#### Common Variants  
- Card-skimming & Magecart web injections  
- SWIFT/ACH fraud via compromised credentials  
- Crypto-exchange theft & ransomware payouts

#### Attack Lifecycle  
1. Recon merchant/payment flows  
2. Credential phishing or malware dropper  
3. Data exfil or funds transfer (often micro-transactions)  
4. Launder via mixers, mule accounts

#### Evidence  
- Spike in small outbound transfers or test payments  
- Web-shells on checkout pages  
- Ransom notes with Bitcoin wallet addresses

#### Controls  
- PCI DSS compliance 😎 (network segmentation, quarterly scans)  
- Fraud analytics & velocity checks  
- Rapid IR playbooks to freeze transfers

### Terrorist Attacks

#### Overview  
*Goal:* ☢️ Spread fear, disrupt critical services, amplify physical terror.

#### Potential Targets  
- Power grids (ICS/SCADA)  
- Transportation systems (rail, aviation, maritime)  
- Public-alert networks & media outlets

#### Tactics  
- Coordinated physical + cyber strikes  
- Malware (e.g., Triton, Industroyer) altering safety systems  
- Destructive wipers (Shamoon family)

#### Indicators  
- Surge in OT/ICS anomalies, malformed PLC commands  
- Propaganda videos claiming responsibility  
- Geopolitically timed to anniversaries/events

#### Mitigation  
- OT network segmentation (“ISA/IEC 62443”)  
- Strict change-control for PLC firmware  
- Gov-industry intel sharing (e.g., ISACs)

### Grudge Attacks

#### Overview  
*Goal:* 😠 Personal vengeance—harm victim’s data, reputation, or operations.

#### Typical Actors  
- Disgruntled ex-employees  
- Rejected partners, embittered competitors

#### Attack Vectors  
- Still-valid VPN or cloud keys (poor deprovisioning)  
- Logic bombs / backdoors planted pre-departure  
- Public doxxing or defamatory leaks

#### Key Evidence  
- Access from familiar internal IPs after termination  
- Sudden data deletion, odd PowerShell scripts  
- “Good-bye.txt” or rant posts on social media

#### Defense  
- Immediate account disablement at separation  
- Privilege reviews, behavioral analytics  
- Regular insider-risk tabletop exercises

### Thrill Attacks

#### Overview  
*Goal:* 🎢 Entertainment, bragging rights, or curiosity.

#### Actors  
- **Script kiddies** using downloadable exploit kits  
- Rookie hackers seeking online reputation (“leet points”)

#### Common Stunts  
- Website defacements (WordPress, Joomla vulnerabilities)  
- Simple DoS floods via booter services  
- Unauthorized Wi-Fi wardriving

#### Evidence  
- Graffiti web pages (“hacked by XYZ”)  
- Amateurish handle in defacement note  
- Loud scanning from residential IPs

#### Countermeasures  
- Patch management & WAF rules  
- Rate-limiting, DDoS mitigation services  
- Security awareness to deter low-hanging social exploits

### Hacktivists

#### Overview  
*Goal:* ⚖️ Advance political/ideological agenda by disrupting or exposing target.

#### Signature Campaigns  
- **DDoS** (e.g., LOIC, Mirai botnets) against gov’t/corporate sites  
- **Data leaks / “doxxing”** to embarrass or coerce policy change  
- Website defacements with manifesto banners

#### Organization Style  
- Loose, anonymous collectives (e.g., Anonymous, LulzSec)  
- Crowd-sourced toolkits shared on pastebins/Telegram

#### Evidence  
- Public countdowns or threats on social media  
- Mass mailing of stolen docs to journalists  
- Botnet traffic with repeating ideological strings

#### Defensive Focus  
- Crisis-comms playbooks & legal review for leaked data  
- Traffic scrubbing via CDN / DDoS providers  
- Monitoring dark-web chatter for early warnings

#### 📝 Exam Tips

1. **Motivation ⇒ Method**: Always link the attacker’s *why* to the *how* when choosing controls in scenario questions.  
2. **Insider ≠ External**: Remember that *grudge* and some *business* attacks can be internal; detection relies on strong IAM & logging.  
3. **APT vs Hacktivist**: Both may be persistent, but APTs seek *stealth* and *intel*, while hacktivists want *visibility* and *impact*.

## Ethics

Information-security professionals occupy positions of **trust**: they safeguard data, influence policy, and often hold privileged access. A formal **code of ethics** helps ensure this power is exercised responsibly.  On the CISSP exam, expect questions that test your knowledge of (1) how ethics guide professional behavior and (2) the content of key ethical frameworks.

### Organizational Code of Ethics

> **Definition**: A high-level statement of expected behavior adopted by an individual employer or government entity.

| Element | Purpose | Example Practice |
|---------|---------|------------------|
| **Loyalty to mission** | Align decisions with org’s highest principles. | “Put loyalty to moral principles above loyalty to department.” |
| **Legal compliance** | Affirm adherence to laws/regulations. | Uphold all federal/state regulations; prohibit participation in evasion schemes. |
| **Duty & diligence** | Encourage honest, efficient work. | “Give a full day’s labor for a full day’s pay.” |
| **Fairness / non-discrimination** | Prevent misuse of authority for favors. | No special privileges, no unjust bias. |
| **Conflict-of-interest avoidance** | Guard against private gain from insider info. | Ban trading on confidential data; bar procurement self-dealing. |
| **Expose corruption** | Commit to whistleblowing when needed. | Employees must report suspected fraud or abuse. |

> 🔑 **Exam angle**: When an org’s policy conflicts with professional codes (e.g., ISC2), the **stricter** or **lawful** standard prevails.  

### ISC2 Code of Professional Ethics

The **ISC²** Code—binding on CISSP holders—contains a **preamble** and **4 canons**.  Memorize the intent of each canon.

| Canon | Focus | Key Questions to Ask Yourself |
|-------|-------|------------------------------|
| **I. Protect society, the common good, public trust, and infrastructure** | Societal responsibility | *“Will this action harm users or critical services?”* |
| **II. Act honorably, honestly, justly, responsibly, and legally** | Personal integrity | *“Am I following the law and being transparent?”* |
| **III. Provide diligent and competent service to principals** | Duty to employer/client | *“Do I have the skills/knowledge to do this task well?”* |
| **IV. Advance and protect the profession** | Continuous improvement & sharing | *“Am I contributing to the security community?”* |

**Complaint Process (high-level):**

```text
Standing   →  Injured party files sworn affidavit
Canon I/II →  Anyone (public) may complain
Canon III  →  Employer/contracting principal only
Canon IV   →  Any licensed/certified professional
Outcome    →  ISC² investigation → sanctions up to cert revocation
```
> **✨ Tip:** On scenario questions, pick the answer that best upholds **all four canons**  
> *(protect society, remain honest, serve the client competently, and advance the profession).*

### Ethics and the Internet

Several historical documents offer broader guidance for online conduct.

#### RFC 1087 – *Ethics & the Internet* (1989)

Unacceptable acts (❌):

- Unauthorized access  
- Disruption of intended use  
- Waste of resources  
- Destruction of information integrity  
- Compromise of user privacy  

#### Ten Commandments of Computer Ethics  
*(Computer Ethics Institute)*

1. Do **no harm**.  
2. Don’t interfere with others’ work.  
3. Don’t snoop in files.  
4. Don’t steal via computer.  
5. Don’t spread falsehoods.  
6. Don’t pirate software.  
7. Don’t use resources without authorization.  
8. Respect intellectual property.  
9. Consider social consequences.  
10. Show respect for fellow humans.  

#### Code of Fair Information Practices (1973)

| Principle                 | Modern Parallel                                   |
|---------------------------|---------------------------------------------------|
| No secret systems         | Data-inventory & transparency requirements        |
| Individual access         | Subject Access Requests (GDPR, privacy laws)      |
| Use limitation / consent  | Purpose-limitation clauses                        |
| Correction / accuracy     | Right to rectification                            |
| Reliability & safeguards  | Security & breach-prevention duty                 |

> 🌐 **Bottom line:** All frameworks converge on **privacy, integrity, accountability, and minimal harm** in cyberspace.

## Summary

- **Codes of ethics = guardrails** for professionals who wield significant technical power.  
- **Organizational codes** address local culture and legal duties; the **ISC² Code** sets industry-wide expectations and is enforceable through certification sanctions.  
- **Internet ethics frameworks** (RFC 1087, Ten Commandments, Fair Information Practices) expand the lens to societal impact, privacy, and responsible resource use.  
- On the exam, always choose actions that:  
  - Protect society & infrastructure,  
  - Maintain honesty & legality,  
  - Serve principals competently, and  
  - Uphold the profession.  

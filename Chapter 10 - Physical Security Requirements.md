# Chapter 10: Physical Security Requirements

- [Apply Security Principles to Site and Facility Design](#apply-security-principles-to-site-and-facility-design)
  - [Secure Facility Plan](#secure-facility-plan)
  - [Site Selection](#site-selection)
  - [Facility Design](#facility-design)
- [Implement Site and Facility Security Controls](#implement-site-and-facility-security-controls)
  - [Equipment Failure](#equipment-failure)
  - [Wiring Closet](#wiring-closet)
  - [Server Rooms/Data Centers](#server-roomsdata-centers)
  - [Intrusion Detection Systems](#intrusion-detection-systems)
  - [Cameras](#cameras)
  - [Access Abuses](#access-abuses)
  - [Media Storage Facilities](#media-storage-facilities)
  - [Evidence Storage](#evidence-storage)
  - [Work Area Security](#work-area-security)
  - [Utility Consideration](#utility-consideration)
  - [Fire Prevention, Detection, and Suppression](#fire-prevention-detection-and-suppression)
- [Implement and Manage Physical Security](#implement-and-manage-physical-security)
  - [Perimeter Security Controls](#perimeter-security-controls)
  - [Internal Security Controls](#internal-security-controls)
  - [Key Performance Indicators of Physical Security](#key-performance-indicators-of-physical-security)
- [Summary](#summary)

---
## Apply Security Principles to Site and Facility Design  
### Secure Facility Plan

#### 🧠 Concept
- A **secure facility plan** outlines the organization's physical security needs.
- Built via **risk assessment** + **critical path analysis** (CPA).
- CPA maps out mission-critical dependencies (e.g., internet, power, HVAC).

#### 🔁 Tech Convergence Risks
- Combining techs (e.g., video + voice + data) into single paths increases efficiency but can create **single points of failure** 🎯.

#### 🧱 Layered Defense Model
- Multiple physical controls work in **series** (not parallel) like an **obstacle course** to resist intrusion.

---
### Site Selection

#### 🔐 Security-Focused Selection
- Security outweighs cost, size, or visibility.
- Consider:
  - 🏘️ Proximity to public areas or noisy/dangerous businesses.
  - 🚨 Distance to emergency responders.
  - 🌪️ Local weather threats & construction durability.

### 🕵️ Industrial Camouflage
- Use misleading building exteriors to hide real purpose (e.g., make a data center look like a factory).

---
### Facility Design
#### 👷 Safety First
- **Main priority:** protect lives.
- Follow all laws (e.g., **OSHA**, **EPA** in the U.S.).
- Include a **facility security officer** for planning & oversight.

#### 📐 Security Features to Consider
- Materials: combustibility, fire rating, strength.
- Environment: HVAC, water/sewage, gas, power.
- Threats: forced entry, alarms, secure exits, airflow.

---
#### 🏙️ CPTED – Crime Prevention Through Environmental Design

##### 🧠 Core Principle
Design can influence behavior to **deter crime** and **reduce fear**.

##### 🌱 CPTED Suggestions
- Short planters (< 2.5 ft), open entrances, benches for observation 👀.
- Visible cameras 🎥, hide delivery areas, keep entrances clear.

##### 🧱 CPTED 1st Generation (Environmental Design)
1. **Access Control** 🛑  
   - Guide entry with lighting, fences, & layout.
   - Create clear zones: public vs. secure areas.

2. **Natural Surveillance** 🔭  
   - Open visibility, lighting, seating to encourage public presence.

3. **Image and Milieu** 🎨  
   - Clean, welcoming environment builds safety perception.

4. **Territorial Control** 🏠  
   - Use signage, landscaping, and decor to show “ownership.”

##### 🧠 CPTED 2nd Generation (Community-Oriented)
1. **Social Cohesion** 🤝  
   - Strong community = less crime.

2. **Community Culture** 🧧  
   - Design aligns with local customs to increase adoption.

3. **Connectivity** 🧩  
   - Paths, parks, social spaces promote visibility & trust.

4. **Threshold Capacity** 🔄  
   - Understand limits of community to absorb change safely.

#### Takeaway 🧠

| Key CISSP Understandings | 💡 Summary |
|--------------------------|------------|
| Physical security is foundational | No control = No security 🔓 |
| Critical Path Analysis (CPA) | Identifies all mission-critical dependencies ⚙️ |
| Technology Convergence | Efficiency ⬆️ = Risk of single failure point ⬆️ |
| Layered Defense | Combine deterrence, delay, detection & response ⛓️ |
| CPTED | Design influences crime deterrence 🏘️ |
| Access Control | Use of physical layout to subtly control movement 🚷 |
| Surveillance | Design for visibility and observation 🕵️‍♀️ |
| Positive Image | Clean, aesthetic environments discourage crime ✨ |

✅ Use this guide to answer scenario-based CISSP questions related to:
- Facility layout
- CPTED strategies
- Planning & design dependencies
- Physical and administrative controls

---

## Implement Site and Facility Security Controls  

### Equipment Failure
* Use **redundant power (UPS + generator)**, dual HVAC, hot/cold aisle containment, MTBF metrics.

### Wiring Closet
* Hardened door, badge + **keyed lock**, logged access, no windows, fire rating 1 hr.

### Server Rooms/Data Centers
* Raised floor (12–24 in) for cooling & cabling; **EMI shielding** (TEMPEST) for classified zones.

### Intrusion Detection Systems
* Glass-break, motion (IR, microwave), vibration sensors; integrate with **SIEM** for SOC alerts.

### Cameras
* 0.1 lux or IR for low-light; **coverage: 50 % overlap, no blind spots**. Store video 30–90 days (policy).

### Access Abuses
* Tailgating → anti-passback + turnstiles.  
* Piggyback detection via weight sensors, biometrics.

### Media Storage Facilities
* Fire-rated cabinets, **Faraday bags** for ESD, chain-of-custody log.  Away from water pipes, HVAC drains.

### Evidence Storage
* Locker with tamper-evident seals, dual-custodian sign-off, **FIPS-140-2 Level 2+ HSM** for key material.

### Work Area Security
* Clear-desk / clear-screen, privacy filters, locked desktops, *screen timeout ≤ 15 min*.

### Utility Consideration
* Dual power grids, isolated ground, dedicated diesel tank (min 24 h runtime), redundant fiber paths.

### Fire Prevention, Detection, and Suppression
* **Classes:** A (solids), B (liquids), C (electrical), D (metals), K (cooking).  
* Detection: ionization (flame), photoelectric (smoke), heat.  
* Suppression:  
  - Water (wet-pipe, pre-action)  
  - Clean agent (FM-200®, Novec 1230, **Inergen**), inert gas for data centers  
  - CO₂ for unoccupied areas  
* Halon legacy → follow **Montreal Protocol** phase-out exam cue.

---

## Implement and Manage Physical Security  

### Perimeter Security Controls
| Layer | Control | Key Metric |
|-------|---------|------------|
| Outer | Fences (7 ft+ = deter), bollards (K-12) | Delay time |
| Mid   | Guard patrols, dogs, CCTV | Response time |
| Inner | Mantraps, biometric locks | False-reject rate |

*Lighting* ≥ 2 fc at gates, 8 ft candle at doors (IESNA standard).

### Internal Security Controls
* **Zone-based** badge readers, secure cabinets, port blockers, cable locks.  
* Focus on *areas of assembly* (labs, SOC) ⇒ duress alarms.

### Key Performance Indicators of Physical Security
* **MTTD / MTTR** for alarms.  
* **Unauthorized entry attempts** per month.  
* **Mean time between power incidents**; **camera uptime %**.  
* Use dashboards for trend & SLA compliance.

---

## Summary
* Physical security underpins every CIA objective—breaches here bypass logical controls.  
* **Layered defenses, CPTED, and environmental controls** form the design baseline.  
* Prioritize life-safety first (NFPA 101), then asset protection.  
* For CISSP, expect scenario questions on selecting the right *fire suppression*, calculating *buffer distances*, and mapping **shared responsibility** between landlord vs tenant for multi-site facilities.




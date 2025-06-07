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
* **Defense-in-Depth** for physical space: concentric rings (perimeter → building → computer room → cabinet).  
* Align zones to **asset value**; place high-value assets in center with more layers.  
* Integrate **CPTED**: natural surveillance, access control, territorial reinforcement, maintenance.

### Site Selection
| Factor | Risk | Control |
|--------|------|---------|
| **Natural hazards** | Floodplain, seismic zone | Elevation, seismic bracing |
| **Man-made threats** | Rail line, protest hotspots | Buffer distance, blast film |
| **Critical infrastructure** | Power, water, telco diversity | Dual feeds, EMP-shielded cables |

> **Exam flag:** Understand *buffer zones* (K-rating standoff) and why multi-tenant buildings complicate isolation.

### Facility Design
* **Single entrance** for staff + guarded shipping/receiving.  
* **Mantraps / turnstiles / visitor escorts** enforce *single-factor* (card) + *secondary* (biometric) auth.  
* HVAC: 68–72 °F (20–24 °C), 40–60 % RH; positive pressure toward secure areas.

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




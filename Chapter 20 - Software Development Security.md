# Chapter 20: Software Development Security

- [Introducing Systems Development Controls](#introducing-systems-development-controls)
  - [Software Development](#software-development)
  - [Systems Development Life Cycle](#systems-development-life-cycle)
  - [Life Cycle Models](#life-cycle-models)
  - [Gantt Charts and PERT](#gantt-charts-and-pert)
  - [Change and Configuration Management](#change-and-configuration-management)
  - [The DevOps Approach](#the-devops-approach)
  - [Application Programming Interfaces](#application-programming-interfaces)
  - [Software Testing](#software-testing)
  - [Code Repositories](#code-repositories)
  - [Service-Level Agreements](#service-level-agreements)
  - [Third-Party Software Acquisition](#third-party-software-acquisition)
- [Establishing Databases and Data Warehousing](#establishing-databases-and-data-warehousing)
  - [Database Management System Architecture](#database-management-system-architecture)
  - [Database Transactions](#database-transactions)
  - [Security for Multilevel Databases](#security-for-multilevel-databases)
  - [Open Database Connectivity](#open-database-connectivity)
  - [NoSQL](#nosql)
- [Storage Threats](#storage-threats)
- [Understanding Knowledge-Based Systems](#understanding-knowledge-based-systems)
  - [Expert Systems](#expert-systems)
  - [Machine Learning](#machine-learning)
  - [Neural Networks](#neural-networks)
- [Summary](#summary)

## Introducing Systems Development Controls

### Internal Security Controls

Effective internal security mechanisms ensure that only authorized individuals gain access to secure zones within a facility.

#### 👥 Visitor Management

- Visitors should be:
  - **Escorted** at all times
  - Logged (manually or automatically)
  - Subject to monitoring via badges, motion detectors, or cameras
- **Reception areas** should:
  - Act as a **choke point**
  - Be segregated from sensitive areas
  - Include locked doors and surveillance systems
- Visitor and **employee logs** are essential for:
  - **Accountability**
  - **Evacuation validation**
  - **Correlation with logical/log access logs**

---

#### 🔐 Keys and Combination Locks

| Lock Type         | Description                                                                   |
|-------------------|-------------------------------------------------------------------------------|
| Preset/Conventional | Simple key-based locks (e.g., deadbolt); low cost, but vulnerable to picking, bumping |
| Programmable       | Support multiple codes and access methods; may use keypad or smartcard       |
| Electronic Access Control (EAC) | Includes magnet, credential reader, and sensor; logs access times and durations |

⚠️ **Attacks**:  
- **Shimming** and **bumping** can bypass conventional locks.

🔔 Example EAC logic:
- Warning buzzer if door is open >5 seconds
- Alarm if open >10 seconds

### Environmental Issues and Life Safety

Human safety takes precedence over all other assets.

#### 🔧 Facility Environmental Stability

- Disruptions in **water, power, HVAC** may lead to broader risks.
- Risks include:
  - Fire
  - Flooding
  - Toxic material release
  - Natural/human-made disasters

#### 👨‍👩‍👧‍👦 Occupant Emergency Plan (OEP)

- Focuses solely on **personnel safety**.
- Covers:
  - Evacuation, duress management, injury prevention
  - Safe travel, basic property protection
- Does **not** address IT systems (those are handled by BCP and DRP)

🧠 **Key Concept**: Always protect **human life first** before addressing business continuity.

### Regulatory Requirements

All organizations are subject to **industry** and **jurisdictional regulations** that affect security operations.

- Areas affected:
  - Software licensing
  - Employment practices
  - Data handling
  - Safety compliance

⚖️ Legal and regulatory compliance forms the **baseline** of any secure infrastructure.

### 📊 Key Performance Indicators of Physical Security

**KPIs** help assess the effectiveness of security controls and guide improvements.

#### 🧮 Common Physical Security KPIs

| Metric Type               | Examples                                                                 |
|---------------------------|--------------------------------------------------------------------------|
| Incidents (Success)       | # of successful intrusions, crimes, disruptions                          |
| Incidents (Failure)       | # of attempted but failed intrusions, crimes, incidents                  |
| Time-Based Metrics        | Detection time, response time, recovery time, return to normal operation |
| Quality Metrics           | Number of false positives, incident severity, organizational impact      |

📈 **KPI Best Practices**:

- **Establish baselines** for all KPIs.
- Maintain **historical records** for trend analysis.
- **Automate** collection when possible.
- Use **incident reviews** to extract lessons learned and improve future response.

📊 With solid KPI data, organizations can:
- Identify weaknesses
- Evaluate control effectiveness
- Perform ROSI (Return on Security Investment)
- Conduct cost–benefit analysis

---

🧠 **CISSP Tip**:
You will likely encounter scenario-based questions on:
- Selecting physical controls for internal vs. external zones
- Responding to personnel or environmental safety concerns
- Understanding the role of OEP vs. BCP/DRP
- Interpreting KPI data for physical security effectiveness

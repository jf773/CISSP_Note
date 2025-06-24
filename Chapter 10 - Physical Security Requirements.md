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

The term *physical controls* in CISSP includes more than physical objects—it encompasses **policies, personnel management, technology, and barriers** for safeguarding facilities.

#### 📌 Categories of Physical Security Controls

| Control Type     | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| Administrative   | Site selection, building design, personnel, emergency procedures 🧑‍💼        |
| Technical        | Alarms, HVAC systems, fire suppression, surveillance, access systems 💡🧯      |
| Physical         | Locks, lighting, fencing, bollards, guards, dogs 🐶🔐                        |

#### 📋 Order of Operations for Physical Security Controls

1. **Deter** 🚫 – Make the facility unappealing to intruders (e.g., signage, fences).
2. **Deny** ❌ – Block access (e.g., locked doors, vaults).
3. **Detect** 👁 – Identify unauthorized activity (e.g., motion sensors).
4. **Delay** ⏳ – Slow intruders to give responders time (e.g., cable locks).
5. **Determine** 🔍 – Understand what happened or is happening.
6. **Decide** 🧠 – Choose the appropriate response (e.g., report, detain).

> 🔐 **Cable locks** are used to protect portable devices—not foolproof, but a deterrent to casual theft.

### Equipment Failure

🔧 **Preparation Options**:
- Replacement parts onsite or vendor SLA for rapid recovery.
- **SLA (Service-Level Agreement)** defines vendor's response time during failures.

🔁 **Planning Considerations**:
- **AIW (Allowable Interruption Window)** ⏱
- **SDO (Service Delivery Objective)** 📦
- **MTD/MTO (Max Tolerable Downtime/Outage)** 🚨

📊 **Lifecycle Metrics**:

| Term  | Meaning                                                                            |
|-------|------------------------------------------------------------------------------------|
| MTTF  | Mean Time to Failure – expected device lifespan before failing. 🕰                 |
| MTTR  | Mean Time to Repair – average time needed to fix a failure. 🔧                     |
| MTBF  | Mean Time Between Failures – time between one failure and the next. 🔄             |

🧠 **Best Practices**:
- Replace hardware before MTTF expiration.
- Have backup or alternate devices ready during repairs.
- Don’t wait for full failure—act early to ensure availability.

---

### Wiring Closets

🏢 **Cable Plant Management Policy** defines secure cable architecture and layout.

#### 🧩 Elements of a Cable Plant

| Component                  | Description                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| Entrance Facility (MDF)    | Main demarcation point from external provider into building 🛣              |
| Equipment Room             | Central location for main wiring closets and network hardware 🖧            |
| Backbone Distribution      | Cross-floor network cable infrastructure 📶                                 |
| Wiring Closet (IDF)        | Serves local floor areas, connects backbone to horizontal wiring 🔌         |
| Horizontal Distribution    | Cables and hardware between closet and end-user systems 🧵                   |

#### 🔐 PDS (Protected Distribution System)

PDS aims to:
- **Deter** unauthorized tampering
- **Detect** intrusion or access attempts
- **Prevent** cable compromise

PDS includes: conduits, sealed joints, and physical inspections.

#### 🧱 Wiring Closet Security Best Practices

- ❌ Don’t use wiring closets for storage.
- 🔒 Install locks—preferably biometric.
- 🧹 Keep the area clean and unobstructed.
- 🔥 No flammable material should be stored.
- 🎥 Install CCTV surveillance.
- 🚪 Door sensors should log all access.
- 🛠 Restrict key access to authorized admins only.
- 👀 Conduct regular physical inspections.
- 🌡 Include in environmental monitoring (fire, flood, temp, humidity).

> 🛑 Notify building management of cable plant access policies to reduce unauthorized entry risk.

#### 📝 CISSP Tip Table: Lifecycle Terms for Equipment Planning

| Term | Full Name | Description | Example |
|------|-----------|-------------|---------|
| MTTF | Mean Time to Failure | How long a device is expected to last before it fails. | Replace drives every 5 years. |
| MTTR | Mean Time to Repair | Average time to fix a failed component. | It takes 2 hours to replace a PSU. |
| MTBF | Mean Time Between Failures | Time between two failures for the same equipment. | One router fails every 300 days. |

### Server Rooms/Data Centers
Server rooms and data centers are **secured, restricted environments** for housing mission-critical IT infrastructure.

- Typically **"lights-out"** zones: low-light, low-temp, optimized for equipment, not humans 💡❄️
- Should be located:
  - **At the core of the building** 🏢
  - **Away from** ground/top floors and water/gas/sewage lines 🌊
- Fire safety: Use **oxygen-displacement fire suppression systems** (e.g., halon substitutes) 🔥
- May be on-premises or hosted externally (e.g., CSP or colocation) 🖧

**Access Control Technologies Used:**
- Smartcards and badges 🔐
- Proximity readers and devices 📶
- Biometrics and IDS 🧬🚨
- **Defense in depth** for layered security 🔁

#### Smartcards and Badges
Used for identification and/or authentication to access secure facilities or systems.

| Type                    | Features                                                                                  | Weaknesses                                                   |
|-------------------------|--------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| **Smartcards**          | Embedded chip, can store/process data; used in MFA                                        | Can be attacked (physical, logical, Trojan, social engineering) |
| **Magnetic Stripe Cards** | Contains limited data, similar to credit card                                              | Easy to duplicate, not secure enough alone                   |
| **Dumb Cards/Badges**   | Printed name/photo only; no electronics                                                    | No authentication or identity verification features           |

- **"Something you have"** factor for authentication 🪪
- Often part of **multifactor authentication (MFA)** 🔐
- Retrieval and destruction required during employee offboarding ❌
- Visitor/day badges must be clearly marked (e.g., bright colors) 🟨

#### Proximity Devices
Used for **touchless access control** with proximity readers.

| Type                    | Power Source              | Description                                                                 |
|-------------------------|---------------------------|-----------------------------------------------------------------------------|
| **Passive Device**      | None                      | Alters EM field generated by reader; like anti-theft tags in stores         |
| **Field-Powered Device**| EM field from reader      | Draws power from EM field; includes many RFID cards                         |
| **Transponder Device**  | Self-powered (battery, solar)| Sends signal to reader; often a button press (e.g., garage door remote)     |

- Wearable or handheld for **automatic identity recognition** 🧷
- Commonly used with **Automatic Request to Exit (AREX)** systems 🚪
  - Senses motion or pressure to auto-unlock exit doors
- Technologies used: **motion sensors, IR, pressure mats** 📡👣

#### 📘 Summary Table: Smartcard & Proximity Comparison

| Feature                  | Smartcards     | Magnetic Stripe | Proximity Devices      |
|--------------------------|----------------|------------------|-------------------------|
| Stores Data              | ✅              | ⚠️ (limited)     | ❌                      |
| Processing Capability    | ✅              | ❌               | ❌                      |
| Read Distance            | ⛔ (insert/swipe)| ⛔ (swipe)        | ✅ (touchless)          |
| Supports MFA             | ✅              | ⚠️ (with PIN)    | ✅ (when paired)        |
| Susceptible to Duplication | ⚠️              | ✅               | ⚠️ (passive devices)    |

📌 **Key Takeaways:**
- Secure server rooms using access control and environmental safeguards.
- Smartcards = versatile, used in MFA, can store/process data.
- Magnetic stripe cards = outdated, limited, easy to clone.
- Proximity devices = touchless convenience, used with RFID/AREX systems.

### Intrusion Detection Systems

Intrusion Detection Systems (IDS) detect unauthorized access or activity within a physical environment. They are a critical layer of defense in facility security.

- **Purpose**: Detect unauthorized entry, alert personnel, and potentially trigger automated defenses.
- **Types of Detection**:
  - **Physical IDS (Burglar Alarms)**: Detect break-ins through doors, windows, or motion in secured areas.
  - **Logical IDS**: Covered in Chapter 17 (related to networks and systems).

#### Power and Communication Requirements ⚡📡
- **Power backup**: At least 24-hour battery power is required.
- **Heartbeat sensors**: Monitor the communication line for tampering (e.g., cut cables).

#### Motion Detectors

| Type                       | Function                                               | Best Use Case                        |
|----------------------------|--------------------------------------------------------|--------------------------------------|
| Digital                    | Detects pattern change in a digital video feed         | Smart camera systems                 |
| Passive Infrared (PIR)     | Detects heat signatures                                | Indoor occupancy monitoring          |
| Microwave / Ultrasonic     | Detects wave pattern disruption                        | Wide area coverage                   |
| Capacitance                | Detects electromagnetic field changes                  | Tamper-sensitive equipment zones     |
| Photoelectric              | Detects visible light level changes                    | Dark, enclosed rooms                 |
| Passive Audio              | Detects unexpected sounds                              | Quiet zones                          |
| Dual-Technology            | Combines PIR and microwave for accuracy                | Reduces false positives              |

#### Perimeter Breach Detection

| Type                  | Description                                                 |
|-----------------------|-------------------------------------------------------------|
| Balanced Magnetic Switch (BMS) | Detects door/window opening using magnetic contact     |
| Infrared Linear Beam  | Detects movement across a defined line or boundary          |

#### Alarm Types

| Type         | Description                                                           |
|--------------|-----------------------------------------------------------------------|
| **Deterrent**  | Engages locks or other barriers to hinder further access              |
| **Repellent**  | Triggers sirens, lights to scare away intruders                      |
| **Notification** | Alerts guards or emergency services, logs the event (often silent)  |

#### Alarm Systems by Location

| System Type       | Audible On-Site | Remote Monitoring | Emergency Service Notification |
|--------------------|------------------|--------------------|-------------------------------|
| Local              | ✅               | ❌                 | ❌                            |
| Central Station    | ❌               | ✅                 | ❌                            |
| Auxiliary          | Optional         | Optional           | ✅                            |

#### Secondary Verification Mechanisms
- 🧠 Use multiple sensors to validate intrusion.
- 📷 Combine alarms with camera systems to reduce false alarms and confirm threats.

### Cameras
Cameras serve both deterrent and evidentiary roles in physical security.

- **Function**: Deter intruders, monitor activities, record events for investigation.
- **Deployment**:
  - Monitor entrances, exits, hallways, and asset locations.
  - Integrate with alarms and motion detectors.
- **Types**:
  - **CCTV**: On-premises closed-loop systems.
  - **IP Cameras**: Network-enabled cameras, often cloud-integrated.
  - **Motion-triggered**: Records when movement is detected.
  - **PTZ (Pan-Tilt-Zoom)**: Remotely controllable cameras.

| Camera Feature     | Description                                                   |
|--------------------|---------------------------------------------------------------|
| Visible Cameras    | Deterrent (obvious presence discourages intruders)            |
| Hidden Cameras     | Detection (covert monitoring)                                 |
| Gait Analysis      | Uses walking patterns for identity verification               |
| SoC Capabilities   | Facial recognition, object tracking, AI analysis              |
| Dummy Cameras      | Cost-effective deterrents without real monitoring             |

- **Storage**: Local DVR/NVR or cloud-based.
- **Risks**: IP cameras may be vulnerable to remote tampering or malware.
- 🔄 Combine with AI/ML for automated threat recognition and reduced false alarms.

### Access Abuses
Even strong physical controls can be undermined through **human behavior or negligence**.

| Abuse Type       | Description                                                                 |
|------------------|------------------------------------------------------------------------------|
| Door Propping    | Leaving doors physically open or jammed to bypass locks                     |
| Tailgating       | Unauthorized person follows an authorized person into a secure area         |
| Piggybacking     | Authorized person knowingly allows unauthorized access                      |
| Impersonation    | Using someone else’s ID or credentials to gain access                       |

#### Prevention & Detection
- **Security Guards**: Physical presence for real-time validation.
- **Audit Trails**: Manual logs or automatic logging with smartcard systems.
- **Security Cameras**: Visual evidence to verify or investigate abuse.
- **Log Elements**:
  - Time of entry request
  - Authentication result
  - Duration of access door opening

📌 Cross-referencing **logs** with **video footage** improves investigation accuracy.

### Media Storage Facilities
Media storage must be secured to prevent theft, data remnant recovery, and malware planting.

#### 🔐 Security Practices
- Store media (blank, reusable, installation) in **locked cabinets**, **safes**, or **vaults**.
- Use a **media librarian/custodian** to manage access.
- Implement **check-in/checkout logs** to track media movement.
- Secure new media to prevent tampering.
- Protect installation media to ensure trusted software deployment.

#### 💾 Reusable Media Risk: Data Remnants
- Simple deletion or formatting does **not** remove data entirely.
- Use **secure wipe** tools or **zeroization** methods.
- Verify sanitization using **hash-based integrity checks**.

#### 🧱 Storage Types
| Type     | Description                              |
|----------|------------------------------------------|
| Safe     | Movable, not part of building structure  |
| Vault    | Fixed, integrated into the building      |

#### 🔖 Advanced Protections
- Label media with **security classification stickers**.
- Use **RFID/NFC** tags for tracking.
- Consider **fire, flood, temperature, and electromagnetic shielding** for critical storage areas.

---

### Evidence Storage
Secure evidence storage supports incident response and forensic investigations.

#### 🔍 Requirements
- Use **dedicated storage systems**, separate from production.
- Keep storage **offline** when not in use.
- **Block internet** access to/from the storage system.
- **Log all activity** and access to stored data.
- **Hash** all stored datasets for integrity checks.
- **Encrypt** all stored data.
- Limit access to **security admins and legal counsel** only.

📌 **Note**: Requirements may vary by regulation, contract, or jurisdiction. See Chapter 19 for legal considerations.

### Work Area Security
The internal design of a facility must ensure that access is based on the principle of **least privilege**.

#### 🧱 Segmentation and Zoning
- Public areas (restrooms, lobby phones) should not provide access to sensitive zones.
- Use **walls and partitions** to:
  - Prevent **shoulder surfing**
  - Physically separate sensitive work areas
- **Floor-to-ceiling walls** and properly sealed ceilings (even above suspended ceilings) are best for sensitive zones.

#### 🧹 Clean Desk Policy
- Instruct employees to store sensitive info (notes, documents, devices) at the end of each workday.
- Prevents:
  - Information disclosure
  - Data theft
  - Unauthorized access

#### 🔐 Classification of Work Areas
- Assign **classification levels** to work areas (like with IT assets).
- Restrict access to those with matching **clearance levels**.
- Apply stricter access to areas with higher sensitivity.

#### 👥 Visitor Management
- Use:
  - Escorts
  - Visitor logs
  - Video monitoring
  - Person traps
  - RFID tags or badges
  - Security guards

#### 🛡️ SCIF (Sensitive Compartmented Information Facility)
A **SCIF** is a secure room/facility designed to handle classified information.

| Attribute           | Details                                                                 |
|---------------------|-------------------------------------------------------------------------|
| Purpose             | Store, view, and process classified SCI (Sensitive Compartmented Info) |
| Access Restriction  | Limited to individuals with **clearance + SCI approval**               |
| Recording Devices   | Usually prohibited (e.g., phones, cameras)                             |
| Deployment          | Ground, airborne, marine; permanent or temporary                       |

🧠 **Remember**: SCIFs are often government or military-operated but may be found in private defense contractors as well.

### Utility Consideration

Ensuring stable, reliable utilities is essential to maintaining the security and operability of critical IT infrastructure.

#### 🔌 Power Considerations

Electricity from the grid is often inconsistent. To ensure reliability, organizations implement various levels of power protection:

| Protection Level          | Description                                                                                 |
|---------------------------|---------------------------------------------------------------------------------------------|
| Surge Protector           | Cuts off power during overload. Only protects against spikes.                              |
| Power Conditioner         | Filters noise and fluctuations in power lines (advanced surge protector).                   |
| UPS (Uninterruptible Power Supply) | Provides surge protection, power conditioning, and battery backup.                     |

##### UPS Types

| Type                 | Characteristics                                                                                 |
|----------------------|-------------------------------------------------------------------------------------------------|
| Double Conversion    | Always routes power through battery → consistent, clean power.                                 |
| Line Interactive     | Switches to battery during failure. May have a brief delay (some devices might reboot).        |

- ⚠ **Design Tips**: Prioritize critical systems for UPS power.
- 🔄 **Generators**:
  - Automatically activate during grid failure.
  - Require fuel (liquid/gas) and maintenance.
  - UPS bridges power until generators stabilize.

##### Common Power Issues (💥 know these for the exam!):

| Term       | Description                          |
|------------|--------------------------------------|
| Fault      | Momentary complete loss              |
| Blackout   | Prolonged complete loss              |
| Sag        | Momentary low voltage                |
| Brownout   | Prolonged low voltage                |
| Spike      | Momentary high voltage               |
| Surge      | Prolonged high voltage               |
| Inrush     | Initial spike when power is applied  |
| Ground     | Safe path for electricity to the earth|

#### 📡 Noise

Noise refers to unwanted electrical interference. It affects data transmission and equipment functionality.

- **Electromagnetic Interference (EMI)**: From electric currents.
- **Radio Frequency Interference (RFI)**: From household/office devices (e.g., lights, heaters, motors).

✅ Mitigation Strategies:
- Use **shielded cables**
- Deploy **fiber optic** for networking
- Apply **grounding**
- Avoid EMI/RFI-heavy zones

#### 🌡 Temperature, Humidity, and Static

**HVAC control** is vital for electronics and servers.

- 📈 **Ideal Temp Range**: 59–89.6°F (15–32°C)
- **Use hot/cold aisles** in data centers for airflow management.
- **Fans** and **heat sinks** pull warm air from devices.

📦 **Plenum Space**:
- Air ducts in ceiling/floor areas.
- Cables must be **plenum-rated** (low smoke/toxic gas in fire).

📉 **Stable Temperature** prevents:
- Chip creep (hardware loosening)
- Solder cracks

💧 **Humidity Control**:
- Optimal RH: **20–80%** (some allow 8–90%)
- **Too high**: condensation → corrosion
- **Too low**: static buildup → **electrostatic discharge (ESD)**

| Static Voltage | Possible Damage                          |
|----------------|-------------------------------------------|
| 40 V           | Circuit/component destruction             |
| 1,000 V        | Monitor scrambling                        |
| 1,500 V        | HDD data loss                             |
| 2,000 V        | System shutdown                           |
| 4,000 V        | Printer/component failure                 |
| 17,000 V       | Permanent hardware damage                 |

#### 📈 Environmental and Condition Monitoring

| Type                 | Description                                                                   |
|----------------------|-------------------------------------------------------------------------------|
| Environmental Monitoring | Tracks temp, humidity, dust, smoke, chemicals, bio/radioactive presence     |
| Condition Monitoring     | Assesses real-time operational status and faults in systems or machinery    |

#### 💧 Water Issues

Water leaks can be devastating:

- **Avoid placing data centers near**:
  - Water lines, landscaping features, or basement locations.
- **Install water-detection sensors** under floors.
- **Know the locations of shutoff valves and drains.**

🌧 Evaluate flood risks:
- Building elevation
- History of water accumulation
- Slope direction of landscape

⚡ Reminder: **Water + electricity = damage & electrocution risk**!

💡 **Key Exam Tip**:
Understanding environmental risks and utility dependencies is crucial. Expect scenario-based questions on UPS types, humidity effects, and ESD.

### Fire Prevention, Detection, and Suppression

Fire protection systems must prioritize **life safety** while also protecting **assets** from damage caused by smoke, heat, flames, and suppression materials.

#### 🔺 Fire Triangle

The **Fire Triangle** represents the elements needed for combustion:

| Element    | Description                            | Suppression Method                       |
|------------|----------------------------------------|------------------------------------------|
| Fuel       | Combustible material                   | Soda acid, dry powders, AFFF             |
| Heat       | Ignition source                        | Water, AFFF                              |
| Oxygen     | Sustains combustion                    | CO₂, halon, clean agents                 |
| Reaction   | Chemical chain reaction                | Halon substitutes, clean agents          |

🧯 **Remove any one element to extinguish the fire.**

#### 🔥 Stages of Fire

| Stage        | Description                                       |
|--------------|---------------------------------------------------|
| Incipient    | Air ionization; no visible smoke                  |
| Smoke        | Visible smoke appears                             |
| Flame        | Visible flames emerge                             |
| Heat         | Intense heat and total combustion environment     |

🎯 **Goal**: Detect and extinguish at the earliest stage possible to minimize damage.

#### 🧑‍🏫 Fire Safety Training

- Train employees on:
  - Fire extinguisher use
  - Evacuation routes (know at least two)
  - CPR, AED, and first aid
  - Emergency shutdowns
- Perform regular drills and simulations.
- Maintain proper signage and evacuation maps.

📍 Establish a **rendezvous point** or check-in system after evacuation.

#### 🔥 Common Fire Causes

- Overloaded power outlets
- Misused heating devices (space heaters, coffee makers) near combustibles

#### Fire Extinguishers

Using the right extinguisher type is essential to safely suppress a fire.

| Class | Type                | Suppression Material                                             |
|-------|---------------------|------------------------------------------------------------------|
| A     | Common combustibles | Water, soda acid                                                |
| B     | Liquids             | AFFF, CO₂, halon, soda acid                                     |
| C     | Electrical          | CO₂, halon                                                      |
| D     | Metals              | Dry powder                                                      |
| K     | Cooking media       | Alkaline agents (potassium compounds for saponification)        |

❌ **Do not use**:
- Water on B, C, or K fires
- Oxygen suppression on Class D fires

#### 🔍 Fire Detection Systems

| System Type         | Trigger Mechanism                                   | Notes                                             |
|---------------------|------------------------------------------------------|--------------------------------------------------|
| Fixed-Temperature   | Activates at preset temperature                      | Common, reliable, uses meltable links or vials   |
| Rate-of-Rise        | Activates when temperature increases rapidly         | Can be triggered by HVAC changes                 |
| Flame-Actuated      | Detects IR energy from flames                        | Fast, costly, high-risk areas                    |
| Smoke-Actuated      | Photoelectric or ionization (using americium)        | Can trigger false alarms from dust or steam      |
| Incipient Detection | Detects combustion chemicals (aspirating sensor)     | Extremely early warning, expensive               |

📍 **Detector Placement**: 
- Raised floors, drop ceilings
- Server rooms, public/private areas
- Elevator shafts, HVAC vents, basements

🔔 **Fire Alarms**: Loud sirens + flashing lights; may auto-notify fire services.

#### 🚿 Water Suppression Systems

| Type         | Description                                                                 |
|--------------|-----------------------------------------------------------------------------|
| Wet Pipe     | Always filled with water; instant release on trigger                        |
| Dry Pipe     | Filled with gas; releases water moments after trigger                       |
| Preaction    | Two-stage: fills on smoke/heat, releases only if sprinklers activate        |
| Deluge       | All sprinklers open; high-volume flood—**not** for electronics              |

✅ **Best for data centers**: **Preaction** systems (lower risk of accidental water damage)

⚠️ **Common failure**: Human error (e.g., valve shutoff)

#### 💨 Gas Discharge Systems

| Gas         | Description                                                                 |
|-------------|-----------------------------------------------------------------------------|
| CO₂         | Removes oxygen; very effective, hazardous to personnel                      |
| Halon       | Disrupts combustion reaction; banned for ozone harm                         |
| FM-200      | Halon substitute, still under phase-out due to environmental concerns       |
| Water Mist  | Reduces temperature; unsuitable for electronic environments                 |

⚠️ **CO₂ Hazards**:
- Asphyxiation at 7.5% concentration
- Often deployed at 34%+

🚷 Use gas systems only in **unoccupied spaces**.

#### 🔧 Damage Considerations

| Threat                 | Description                                                       |
|------------------------|-------------------------------------------------------------------|
| Smoke and Soot         | Corrosive, harmful to electronics                                 |
| Heat                   | Tape damage at 100°F, hardware at 175°F, paper at 350°F          |
| Suppression Medium     | Water and powders may short-circuit or corrode components         |
| Firefighters’ Actions  | May cause structural/equipment damage during rescue               |

📌 Even **minor fires** may trigger IRP, BCP, or DRP responses.

🧠 **Key Exam Reminders**:

- Know each fire stage and suppression system type.
- Identify where each suppression method is appropriate.
- Recognize safety procedures (e.g., training, evacuation).
- Understand limitations of water vs. gas suppression.

## Implement and Manage Physical Security  
Effective physical security includes **controlling access**, **monitoring activity**, and **protecting assets** at both the perimeter and interior levels.

### Perimeter Security Controls

#### 🏁 Area Classification

- Areas should be clearly marked as:
  - **Public**
  - **Private**
  - **Restricted**
- Each zone requires unique physical access controls.

#### 🪧 Signage

- Used to deter trespassing, guide behavior, and indicate surveillance.
- Include both physical signs and **digital warning banners**.
- Can support legal enforcement of access restrictions.

#### 📅 Control Testing

- Regularly test: locks, gates, fences, cameras, turnstiles, person traps.
- If not required by regulation, **self-impose a testing schedule**.

#### 🚧 Fences, Gates, Turnstiles, and Person Traps

| Barrier Type      | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| Fence (3–4 ft)     | Deters casual trespassers                                                   |
| Fence (6–7 ft)     | Deters most intruders                                                       |
| Fence (8+ ft + barbed wire) | Deters determined attackers                                       |
| PIDAS              | Multi-layered fence with detection & patrol corridors (used in military)   |
| Gate               | Entry point, must match the strength of the fence                          |
| Turnstile          | Allows one-way access to one person at a time                              |
| Person Trap        | Two-door system preventing tailgating; requires authentication             |

🛡️ **Delay Feature**: Person traps can hold individuals until security arrives.

#### 🛑 Security Bollards and Barricades
- Prevent **vehicle-based intrusions** (e.g., ramming).
- Examples: K-rails, planters, tire shredders, zigzag lanes.
- Use around fuel storage, generators, and critical infrastructure.

#### 💡 Lighting
- Purpose: **Deter** casual intruders, improve visibility for cameras and personnel.
- Deploy at:
  - Entrances, walkways, parking lots
  - Interior access points
- **Emergency lighting**: Should activate on power loss or fire alarms.
- **Best Practice**:
  - ≥ **2 foot-candles (≈ 20 lux)** of illumination
  - Light poles spaced to ensure overlap (about 10–20% closer than the radius)

⚠️ Avoid:
- Lighting **guards or cameras directly** (blinding effect)
- Creating shadows intruders can hide in

### Internal Security Controls

#### 🧍 Security Guards
- **Strength**: Human judgment and response
- Can patrol, monitor, and adapt to evolving threats
- Should perform **random** patrol intervals

#### ⚠️ Limitations
- Susceptible to illness, distraction, manipulation
- Vary in reliability
- Expensive to maintain
- May lack operational awareness (which helps maintain confidentiality)

#### 🐕 Guard Dogs
- Effective for **perimeter detection and deterrence**
- Require:
  - Training
  - Housing
  - Insurance coverage
- High maintenance and liability

#### 🤖 Robot Sentries

- Can be ground-based or UAV (drones)
- Use AI & facial recognition to detect anomalies
- Automated patrol capability; lower maintenance than dogs or humans

🧠 **Key CISSP Takeaways**:

- Physical security relies on a combination of **deterrents, barriers, and human intervention**.
- Understand:
  - The right **fence height** for deterrence
  - When to use **person traps** vs. turnstiles
  - How **lighting placement** affects both deterrence and operational effectiveness
- Consider the **cost–benefit trade-off** for human vs. canine vs. robotic security.

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

#### Environmental Issues and Life Safety

Human safety takes precedence over all other assets.

##### 🔧 Facility Environmental Stability

- Disruptions in **water, power, HVAC** may lead to broader risks.
- Risks include:
  - Fire
  - Flooding
  - Toxic material release
  - Natural/human-made disasters

##### 👨‍👩‍👧‍👦 Occupant Emergency Plan (OEP)

- Focuses solely on **personnel safety**.
- Covers:
  - Evacuation, duress management, injury prevention
  - Safe travel, basic property protection
- Does **not** address IT systems (those are handled by BCP and DRP)

🧠 **Key Concept**: Always protect **human life first** before addressing business continuity.

##### Regulatory Requirements

All organizations are subject to **industry** and **jurisdictional regulations** that affect security operations.

- Areas affected:
  - Software licensing
  - Employment practices
  - Data handling
  - Safety compliance

⚖️ Legal and regulatory compliance forms the **baseline** of any secure infrastructure.

### Key Performance Indicators of Physical Security

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

🧠 **CISSP Tip**:
You will likely encounter scenario-based questions on:
- Selecting physical controls for internal vs. external zones
- Responding to personnel or environmental safety concerns
- Understanding the role of OEP vs. BCP/DRP
- Interpreting KPI data for physical security effectiveness




# Chapter 18: Disaster Recovery Planning

- [The Nature of Disaster](#the-nature-of-disaster)
  - [Natural Disasters](#natural-disasters)
  - [Human-Made Disasters](#human-made-disasters)
- [Understand System Resilience, High Availability, and Fault Tolerance](#understand-system-resilience-high-availability-and-fault-tolerance)
  - [Protecting Hard Drives](#protecting-hard-drives)
  - [Protecting Servers](#protecting-servers)
  - [Protecting Power Sources](#protecting-power-sources)
  - [Trusted Recovery](#trusted-recovery)
  - [Quality of Service](#quality-of-service)
- [Recovery Strategy](#recovery-strategy)
  - [Business Unit and Functional Priorities](#business-unit-and-functional-priorities)
  - [Crisis Management](#crisis-management)
  - [Emergency Communications](#emergency-communications)
  - [Workgroup Recovery](#workgroup-recovery)
  - [Alternate Processing Sites](#alternate-processing-sites)
  - [Database Recovery](#database-recovery)
- [Recovery Plan Development](#recovery-plan-development)
  - [Emergency Response](#emergency-response)
  - [Personnel and Communications](#personnel-and-communications)
  - [Assessment](#assessment)
  - [Backups and Storage Strategies](#backups-and-storage-strategies)
  - [Software Escrow Arrangements](#software-escrow-arrangements)
  - [Utilities](#utilities)
  - [Logistics and Supplies](#logistics-and-supplies)
  - [Recovery vs. Restoration](#recovery-vs-restoration)
- [Training, Awareness, and Documentation Testing and Maintenance](#training-awareness-and-documentation-testing-and-maintenance)
  - [Read-Through](#read-through)
  - [Tabletop](#tabletop)
  - [Walk-Through](#walk-through)
  - [Simulation Test](#simulation-test)
  - [Parallel Test](#parallel-test)
  - [Full-Interruption Test](#full-interruption-test)
  - [Lessons Learned](#lessons-learned)
  - [Maintenance](#maintenance)
  - [Test Communications](#test-communications)
- [Summary](#summary)

## The Nature of Disaster

Disaster Recovery Planning (DRP) kicks in the **moment IT can’t support mission-critical processes**.  A well-designed plan must recognize *every* type of disruptive event and prescribe **pre-approved actions** to restore service quickly.

| Key Term | CISSP-worthy Definition |
|----------|------------------------|
| **Disaster** | Any event that stops, prevents, or threatens normal operations. |
| **BCP vs. DRP** | BCP = business-focused continuity; DRP = *technical* restoration/controls. Most orgs blend both under *Business Continuity Management (BCM)*. |

### Natural Disasters

Natural threats stem from forces **outside human control** yet vary by region, predictability, and impact.  DRP must plan for *both* slow-onset and sudden events.

| Hazard | Predictability | Primary Impacts | DR Countermeasures |
|--------|---------------|-----------------|--------------------|
| **Earthquakes** 🌎 | *Low* (seconds of warning) | Structural failure, power loss | Seismic engineering, off-fault data centers, alternate comms. |
| **Floods / Flash Floods** 🌊 | Medium (flood maps, weather) | Water damage, long downtime | Site elevation, waterproof vaults, FEMA flood insurance, cloud backups. |
| **Storms** (hurricanes, tornadoes, hail, lightning) 🌪️ | Medium–High | Wind damage, surge, debris | Reinforced roofs, surge protectors, WAN diversity, weather monitoring. |
| **Wildfires** 🔥 | Medium | Fire/smoke, evacuation | Fire-resistant landscaping, HEPA filtration, redundant sites. |
| **Pandemics** 😷 | High (weeks) | Workforce unavailability | Remote work, split teams, PPE stockpiles, pandemic insurance review. |
| **Other Local Events** (volcanoes, tsunamis, avalanches, mudslides) | Variable | Regional devastation | Geographic risk assessment, expert consultation, multi-region cloud. |

> 🔑 **Exam tip:** For *flood maps*, remember **100-year floodplain = 1 % annual risk**; letter zones are *not* testable.

#### Earthquakes
* Shifting tectonic plates; high-risk along known faults (e.g., San Andreas).  
* **Design**: seismic racks, automatic gas shut-off, SAN replication to out-of-state site.

#### Floods
* Slow-rise vs. flash floods; tsunami = seismic + flood energy.  
* **Insurance**: U.S. firms often need separate **NFIP** flood policy.

#### Storms
* Hurricanes/tornadoes = wind + flying debris; lightning = surge/burn.  
* **Monitor**: National Hurricane Center for early prep.

#### Fires (Wildfire)
* Climate change ↑ frequency; unpredictable spread.  
* **Preparation**: cleared defensible space, redundant power/communications.

#### Pandemics
* Disrupt people, not buildings. **DR focus = human continuity**: health policies, remote access, essential-worker tiers.

### Human-Made Disasters

Man-made events arise from **intentional actions or human error**.  They often require *multi-disciplinary* mitigation (cybersecurity, physical security, HR, legal).

| Threat | Typical Origin | DR/BC Considerations |
|--------|---------------|----------------------|
| **Structural Fires** 🔥 | Faulty wiring, arson | Fire suppression (clean agent), NFPA codes, off-site hot site. |
| **Terrorism / Bombings** 💣 | Intentional | Hardened perimeters, blast film, insurance riders (terror exclusions!). |
| **Power Outages** ⚡ | Grid failure, storms, sabotage | UPS tests, fuel contracts, generator ATS, load shedding. |
| **Network / Utility Failures** 📡 | ISP cut, water/gas disruption | Diverse carriers, dual entrances, wireless backup, potable-water stock. |
| **Hardware / Software Failures** 🖥️ | Wear, bugs, misconfig | Redundant parts, spare inventory, remote mirroring. |
| **Strikes / Picketing** ✊ | Labor actions | Cross-training, temp staffing, executive engagement. |
| **Theft / Vandalism** 🛠️ | Copper theft, device loss | CCTV, asset tags, secure storage, incident insurance. |

#### Fires (Human-Caused)
* 1 000+ building fires/day (U.S.).  
* **Key DR tasks**: contain quickly, relocate staff, restore IT from off-site media.

#### Acts of Terrorism
* Post-9/11 emphasis on *unpredictable, high-impact* scenarios.  
* **Insurance caveat**: verify terrorism coverage; riders can be costly.

#### Bombings / Explosions
* Gas leaks or hostile devices.  
* **Prevention** via physical security; **response** parallels large fires.

#### Power Outages
* Short vs. sustained loss.  
* Calculate **fuel horizon** aligned to RTO (48 h, 7 d, etc.). Test UPS capacity/load annually.

#### Network / Infrastructure Failures
* Treat Internet, water, roads as *utilities*.  
* Dual fiber paths or satellite; ensure alternate site network capacity.

#### Hardware / Software Failures
* Fully redundant failover servers ideal but $$; otherwise keep on-hand spares and vendor SLAs.

#### Strikes / Picketing
* HR-led; DR ensures minimal disruption: remote support, contract labor pools.

#### Theft / Vandalism
* High pilferage parts (RAM, mobiles) need secure inventory and checkout logging.  
* **Training** reduces risky end-user behavior (e.g., unsecured laptops).

### Exam Hot-List ✅

1. **Identify** which natural threat is most likely for a region and choose the *correct* mitigation (e.g., seismic racks vs. flood barriers).  
2. Know that **terrorism insurance** may be *excluded* unless purchased separately.  
3. Map **pandemic planning** to workforce / supply-chain continuity rather than facility loss.  
4. Differentiate **utility outage planning** from simple power loss (water, gas, telecom counted!).  
5. Recognize that **DRP should reduce real-time decision-making**—pre-approved, autopilot runbooks.  

Master these disaster categories and you’ll ace any CISSP question on *“The Nature of Disaster.”* 🌟

## Understand System Resilience, High Availability, and Fault Tolerance

### Protecting Hard Drives

#### RAID Overview

| RAID Level | Mechanism | Min. Disks | Survives Failures? | Performance | Typical Use |
|------------|-----------|------------|-------------------|-------------|-------------|
| **0** | Striping only | 2 | **None** | ⚡ Highest | Temp scratch, caching |
| **1** | Mirroring | 2 | 1 disk | 🚀 Reads ↑; writes ↔ | OS volumes, logs |
| **5** | Striping + *single* parity | 3 | 1 disk | Balanced | File/DB servers |
| **6** | Striping + *dual* parity | 4 | 2 disks | Write penalty ↓ | Large arrays |
| **10** | Stripe of mirrors (1 + 0) | 4 | 1 disk per mirror set | Very high | High-I/O DB/E-com |

> 🔑 **Exam tip:** RAID ≠ backup!  RAID protects against **hardware** loss; backups protect against *deletion, corruption, or site loss*.

* **Hardware vs. Software RAID**  
  * Hardware = dedicated controller, hot-swap, spare drive slots, better perf (preferred for critical assets).  
  * Software = OS-managed, cheaper, CPU overhead.

#### Spare Strategies
* **Hot spare** – already in chassis; controller auto-rebuilds.  
* **Cold spare** – kept on-site; requires manual swap (and possibly downtime).

### Protecting Servers

#### Clustering

| Cluster Type | Description | FT Benefit | Notes |
|--------------|-------------|-----------|-------|
| **Failover (active/passive)** | One node active, others standby. | Seamless takeover on failure. | DB clusters, file servers. |
| **Load-balancing (active/active)** | Requests distributed across nodes. | Handles node loss & scaling. | Web/app tiers; often front-ended by a load balancer. |

* **Automatic health checks** detect node failure and trigger *failover* or *drain-stop*.  
* **Geographic dispersion** (different regions/AZs) shields against local disasters 🌏.

#### Other Redundancy Patterns
* **Replicated domain controllers** (AD)  
* **Database replication**: master–slave, multi-master, log shipping, etc.  
* **Container / serverless scaling** in cloud IaaS/PaaS.

### Protecting Power Sources

| Control | Purpose | Runtime | Notes |
|---------|---------|---------|-------|
| **UPS (offline/standby)** | Surge + short backup | ≈ 5–10 min | Cheapest; small loads. |
| **UPS (line-interactive)** | Brownout correction + battery | ≈ 15–30 min | SMB servers, network gear. |
| **UPS (online/double-conversion)** | Continuous conditioned power | 15–45 min | Critical data-center racks. |
| **Generator** | Long-term power | Hours–days (fuel-dependent) | Automatic Transfer Switch (ATS) for seamless cutover. |

> ⚠️ **Fuel logistics** are part of DR planning: contracts, delivery priority, and on-site reserves.

### Trusted Recovery

Ensures the **security posture is preserved** after a crash.

| Recovery Mode (per Common Criteria) | Automation | Key Characteristics |
|-------------------------------------|------------|---------------------|
| **Manual Recovery** | None | Admin must secure & validate system post-crash. |
| **Automated Recovery** | Partial | System restores itself from select failures. |
| **Automated Recovery *without undue loss*** | Enhanced | Adds data-integrity checks, log replay, corrupted-file repair. |
| **Function Recovery** | Targeted | Recovers specific functions or rolls back changes to keep system secure. |

* **Fail-secure** vs. **fail-open**: choose availability 🔄 vs. confidentiality 🔒 priorities.  
* Force reboot into *single-user/non-privileged* mode for integrity checks before returning to service.

### Quality of Service

QoS mechanisms **prioritize** and **shape** traffic to uphold *availability* for business-critical flows.

| Factor | Meaning | Management Technique |
|--------|---------|----------------------|
| **Bandwidth** | Max throughput | Rate limiting / reservations |
| **Latency** | Delay per packet | Prioritized queuing |
| **Jitter** | Variance in latency | Buffering, traffic smoothing |
| **Packet Loss** | Dropped frames | Forward-error correction, priority drops |
| **Interference** | Signal corruption | Shielding, channel selection |

Use **Differentiated Services Code Point (DSCP)** or **802.1p** to mark traffic classes (voice, video, transactional, bulk).  
Example: prioritize **VoIP** packets 🔊 over best-effort web browsing.

#### “Nines” Reference

| Availability (n nines) | Max Downtime / Year | ≈ Downtime / Month |
|-----------------------|---------------------|--------------------|
| 99 % (two) | 3 days 15 h | 7 h 18 m |
| 99.9 % (three) | 8 h 45 m | 43 m 12 s |
| 99.99 % (four) | 52 m 33 s | 4 m 19 s |
| 99.999 % (five) | 5 m 15 s | 26 s |

> 🎯 **Remember:** Meeting tighter SLAs demands proportionally higher investment in redundant design, monitoring, and rapid incident response.

#### Exam Hot-List ✅

1. **Identify an SPOF** in a given architecture and choose the correct mitigation (RAID, clustering, UPS, etc.).  
2. Differentiate between **HA** (rapid recovery) and **FT** (no interruption).  
3. Calculate **allowed downtime** for 99.9 % or 99.999 % uptime targets.  
4. Map **RAID levels** to fault-tolerance and performance characteristics.  
5. Pick the correct **trusted-recovery** category for a scenario.  
6. Recognize when **QoS** is the right control to ensure availability under load.

Good luck—master these core ideas, and any Chapter 18 question on resilience, availability, and fault tolerance should be a breeze! 🚀

## Recovery Strategy

A **Recovery Strategy** defines *how* your DRP transitions from crisis to normal operations, specifying *who* to recover **first**, *where* to process workloads, and *how* to restore data.

| Core Element | What It Addresses | CISSP Lens |
|--------------|------------------|------------|
| **Business Unit / Functional Priorities** | *Who* gets re-started first | Driven by BIA, RTO, RPO |
| **Crisis Management** | Leadership & coordination | Calms panic; activates plan |
| **Emergency Communications** | Internal & external messaging | Maintains trust & direction |
| **Workgroup Recovery** | People & workspace logistics | “IT is useless if staff can’t work” |
| **Alternate Processing Sites** | *Where* IT runs during outage | Hot vs. Warm vs. Cold etc. |
| **Database Recovery** | RPO-compliant data sync | Vaulting, journaling, mirroring |

### Business Unit and Functional Priorities

* Use the **Business Impact Analysis (BIA)** to rank units & processes by:
  * **MTTR** (mean time to repair)  
  * **MTD** (max tolerable downtime)  
  * **RTO** (recovery time objective)  
  * **RPO** (recovery point objective)

| Priority Step | Action Item |
|---------------|------------|
| 1️⃣ Identify critical *units* aligned to mission. |
| 2️⃣ Break units into discrete **processes**; rank each. |
| 3️⃣ Allocate recovery resources to hit RTO/RPO targets. |
| 4️⃣ Re-evaluate after major org / tech changes. |

> 🔑 **Exam tip:** Prioritization list is often a **superset** of critical units *plus* cross-cutting functions.

### Crisis Management

* **Goal:** Provide steady leadership, minimize chaos.
* **Crisis Team Roles:** Incident Commander, Safety Officer, Communications Lead, IT/DR Lead, HR Liaison.
* **Key Actions:**  
  * Immediate life-safety measures 🔔  
  * Situation assessment & DRP activation  
  * Stakeholder briefings (execs, regulators, customers)  
* **Training:** Regular drills ensure first-noticers (guards, technicians) know notification trees and initial actions.

### Emergency Communications

| Channel | Use Case | Resilience Control |
|---------|----------|--------------------|
| Voice (cell/landline) | Exec calls, hotline | Diverse carriers, auto-failover PBX |
| SMS / Mass-alert | Blast to employees 📲 | SaaS alerting platform, geo-routing |
| Email / Intranet | Detailed status updates | Cloud mail, O365/AWS WorkMail |
| Satellite / Radio | Last-mile fallback | Deploy to command staff |
| Media / Social | Public statements | Trained PR team, pre-approved scripts |

* **Policy:** All media queries → Public Relations to prevent misinformation.
* **Prep:** Assume primary telco may be down—preposition alternate devices.

### Workgroup Recovery

* **Objective:** Re-establish *people* productivity.
* Approaches:
  1. **Relocation** to sister site / partner office.
  2. **Mobile site** trailers 🚚 for small teams.
  3. **Remote work** activation (VPN, VDI, SaaS).
* **Considerations:** desks, power, connectivity, transportation, childcare, ADA needs.

### Alternate Processing Sites

| Site Type | Ready-State | Data & Apps | Typical RTO | Cost 💲 | Notes |
|-----------|------------|-------------|-------------|---------|-------|
| **Hot** 🔥 | Fully equipped, live | Real-time replicated | Seconds–minutes | $$$$ | Highest resilience; duplicate OpEx |
| **Warm** 🌤️ | Equipped, but no live data | Load backups on event | Hours (≥12 h) | $$$ | Lower telco & license cost |
| **Cold** ❄️ | Space + power/HVAC only | Ship HW + restore | Days–weeks | $$ | Long activation, hard to test |
| **Mobile** 🚚 | Trailer, self-contained | Varies (cold–warm) | Hours–days | $$–$$$ | Good for small workgroups |
| **Cloud DR** ☁️ | On-demand IaaS | VM images / snapshots | Minutes–hours | Pay-as-use | Needs capacity agreement |
| **Mutual Aid (MAA)** 🤝 | Reciprocal partner | Depends on pact | Variable | Low | Risk: same hazard zone, trust issues |

> ⚠️ **Contractual must-have:** *“No lock-out”* clause for shared sites and MAAs.

### Database Recovery

| Method | Data Currency | Mechanism | Pros | Cons | Best For |
|--------|--------------|-----------|------|------|----------|
| **Electronic Vaulting** 📦 | Hours–days | Bulk backup file transfer | Cheap, simple | Large data gap vs. RPO | Low-transaction systems |
| **Remote Journaling** 📑 | ≤1 h | Frequent log shipping | Smaller RPO, bandwidth-light | Restore time (apply logs) | Medium RTO/RPO targets |
| **Remote Mirroring** 🪞 | Seconds | Live transaction replication to standby DB | Near-zero RPO, quick failover | High cost, network load | Mission-critical hot sites |

* **Align choice to RPO:** Over-engineering beyond RPO wastes budget; under-engineering incurs risk.  
* **Test** restore procedures regularly—surprise drills validate staff & tooling.

### Exam Hot-List ✅

1. Map **site types** to correct RTO/RPO & budget scenario.  
2. Choose the right **database recovery** method for given RPO (< 1 hr → journaling; seconds → mirroring).  
3. Distinguish **crisis management** (people/process) from IT restoration.  
4. Identify **communication gaps** (e.g., single telco provider) and suggest redundancy.  
5. Calculate priority order using **BIA metrics** (RTO/RPO vs. MTTR/MTD).  

Master these strategy layers and you’ll handle any CISSP item on “Recovery Strategy” with confidence! 🚀

## Recovery Plan Development

A written DRP must **translate priorities into actionable steps** that any responder can follow under stress.  Good plans combine *concise checklists* for first-responders, *technical guides* for IT, and a *high-level summary* for execs/PR.

| Plan Component | Audience | Purpose |
|----------------|----------|---------|
| Executive summary | Executives, PR | High-level, non-technical view |
| Department playbooks | Business leads | Unit-specific tasks & dependencies |
| Technical guides | IT/engineering | How-to for backup, failover, cloud spin-up |
| Checklists | First responders | Ordered actions in crisis |
| Full DRP | DR team core | Master reference during activation |

### Emergency Response

* **Goal:** Protect life, limit damage, and *formally declare* the disaster.  
* **Checklists** must be **priority-ordered** – top items most likely to be executed when time is short.  
* **Common elements**:  
  1. Life-safety actions (alarm, evacuation)  
  2. Emergency services call (fire/police/EMS)  
  3. Critical-system shutdown or safe-mode  
  4. *Declaration authority* (who can invoke DRP?)  
  5. Initial status report to Crisis Management

> 🔑 **Exam cue:** Declaration criteria & authority must be *pre-defined*; ad-hoc declarations cause confusion.

### Personnel and Communications

| Contact Sheet Must Include | Why |
|----------------------------|-----|
| Primary & alternate for each DR role | Coverage if someone is unreachable |
| Multi-factor reach (cell, SMS, alt email) | Telco failures are common |
| Notification trees or automated alert SaaS | Speed + audit trail |
| Media / PR delegation | One voice to public, avoid rumor |

* **Checklists** keep responders calm and on-task 📋.  
* **Drills** verify that numbers are current and trees flow in < 15 min.

### Assessment

* **Triaging Loop**: *Observe ➜ Assess ➜ Prioritize ➜ Act ➜ Re-assess*.  
* Initial quick survey -> Is site safe? Which systems compromised?  
* Ongoing assessments guide **resource allocation** and update leadership dashboards.

### Backups and Storage Strategies

| Backup Type | What It Captures | Archive Bit / Timestamp | Restore Steps | Storage & Bandwidth |
|-------------|------------------|-------------------------|---------------|---------------------|
| **Full** | Every file | Resets | 1 file set | Largest / slowest |
| **Incremental** | Changes since **last full OR incremental** | Resets | Full + *all* incrementals | Small daily size |
| **Differential** | Changes since **last full** | *Does not* reset | Full + latest differential | Grows each day |

* **Media rotation**: GFS, Tower of Hanoi, 3-2-1 rule (3 copies, 2 media, 1 off-site).  
* **Disk-to-Disk (D2D)** & **Virtual Tape Library (VTL)** replace aging tape; ensure **geo-diverse replicas**.  
* **Cloud backup** adds elasticity—watch for *jurisdiction* & *egress costs*.  
* **Testing**: Surprise restores validate both media *and* staff readiness.

> 🎯 **Exam tip:** Differential = faster restore, Incremental = faster backup.

### Software Escrow Arrangements

| Element | Description |
|---------|-------------|
| **Source code held by 3rd party** | Protects customer if vendor folds or stops support |
| **Trigger events** | Bankruptcy, SLA breach, merger, etc. |
| **Customer rights** | Access code to fix bugs or continue dev |
| **Best fit** | Niche or custom apps with high operational impact |

Large vendors rarely agree, but small ISVs may.  Evaluate during *procurement* and record in DRP asset list.

### Utilities

* Keep **account numbers + 24 × 7 escalation contacts** for: power, water, gas, telco, ISP.  
* Document **generator start-up**, fuel suppliers, water storage, sewer work-arounds.  
* For cloud-centric firms, treat *Internet transit* as a utility—dual carriers, diverse paths.

### Logistics and Supplies

| Need | DR Considerations |
|------|------------------|
| **People movement** | Transport routes, badges/pass lists, shelter-in-place vs. relocation |
| **Workspace** | Desks, ventilation, ergonomic gear at alternate site |
| **Sustainment** | Food, potable water (4 L / person / day), bedding |
| **IT spares** | Drives, NICs, cables—on-site & cache at recovery site |
| **Fuel & fleet** | Contracts for diesel/gas, delivery SLAs |
| **Records** | Paper forms, offline reference docs if networks fail |

### Recovery vs. Restoration

| Phase | Objective | Team | Time Horizon |
|-------|-----------|------|--------------|
| **Recovery** | Bring *processes* & IT online at alternate site to meet RTO | DR (recovery) team | Hours–days |
| **Restoration / Salvage** | Return operations to **primary** site (or new HQ) and verify stability | Salvage team | Days–months |

*Recovery* meets business continuity targets; *Restoration* returns to long-term normal. Both phases must be planned—migration back can itself be disruptive.

#### Exam Hot-List ✅

1. Identify correct **backup type** and restore sequence for given RPO/RTO.  
2. Know when to use **software escrow** and what triggers release.  
3. Distinguish **recovery** (alternate site) vs. **restoration** (primary rebuild).  
4. Recognize critical fields on **utility contact sheets** and *why* redundant carriers matter.  
5. Apply checklist principle: **highest-priority tasks first** because the list may be cut short in real events.

Master these recovery-plan elements and you’ll handle any CISSP question on plan development with confidence! 🚀

## Training, Awareness, and Documentation Testing and Maintenance

### Read-Through
* **What it is:** Paper or PDF review by DR team.  
* **Goals:**  
  * Refresh responsibilities 🧠  
  * Spot outdated contacts/processes  
  * Detect “orphan” tasks after staff turnover  
* **Best for:** Low-cost, frequent validation.

### Tabletop
* **Format:** Role-play scenario in a conference room.  
* **Moderator:** Presents evolving disaster details unknown to team.  
* **Outcome:** Verbal decision-making → identifies plan gaps & coordination issues without operational impact.

### Walk-Through
* **Scope:** Physical or virtual movement; may require staff to exit building, connect remotely, or verify off-site resources.  
* **Value:** Tests logistics (badges, VPN, transport routes) without touching production workloads.

### Simulation Test
* **Action:** Execute selected DR tasks in real time on *non-critical* systems; may pause minor processes.  
* **Checks:** Backup restore speed, script accuracy, run-book usability.

### Parallel Test
* **Process:** Activate alternate site; run workloads *in parallel* while primary continues production.  
* **Advantages:** Validate site readiness, data sync, staff procedures—no customer impact.  
* **Metric:** Compare output consistency between sites.

### Full-Interruption Test
* **Description:** Shut down primary site and shift ALL operations to recovery site, then fail back.  
* **Risks:** Highest—needs exec sign-off, regulatory notice, customer comms.  
* **When used:** Mature DR programs targeting *five-nines* availability.

| DR Test Type | Operations Disrupted? | Confidence Gained | Relative Cost |
|--------------|----------------------|------------------|---------------|
| Read-Through | None | Low | $ |
| Tabletop | None | Medium | $ |
| Walk-Through | Minimal | Medium | $$ |
| Simulation | Minor systems | High | $$ |
| Parallel | None at primary | Very High | $$$ |
| Full-Interruption | Full shutdown | Maximum | $$$$ |

### Lessons Learned
* Held ASAP post-incident/test; facilitated by neutral party.  
* **NIST SP 800-61 questions** drive discussion: What happened? Were procedures adequate? What to improve?  
* **Deliverable:** Written report → feeds plan updates, training, tooling.

### Maintenance
* Treat DRP as **living document**.  
* **Triggers for update:** Infrastructure change, org restructure, regulatory shifts, test findings.  
* **Tools:** Change-management tickets, version control, secured intranet plus *printed* copies at all sites.

### Test Communications
* **Pre-Test:** Notify stakeholders of scope, timing, risks.  
* **During:** Send status updates, incident numbers, ETA for completion.  
* **Post-Test:** Debrief + distribute results; archive records for auditors.  
* **Regulatory angle:** Some sectors (finance, healthcare) require advance notice & evidence of testing.

## Summary
Effective DRP execution relies on **trained people, current documents, and rigorously tested procedures.**  
Regularly scheduled read-throughs, tabletops, and walk-throughs keep knowledge fresh, while simulation, parallel, and full-interruption tests validate technical readiness. Lessons-learned sessions feed an ongoing maintenance cycle, ensuring the plan evolves with the organization and continues to meet business and regulatory requirements.

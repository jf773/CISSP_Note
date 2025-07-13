# Chapter 3 - Business Continuity Planning

- [Planning for Business Continuity](#planning-for-business-continuity) – p 114  
- [Project Scope and Planning](#project-scope-and-planning) – p 115  
  - [Organizational Review](#organizational-review) – p 116  
  - [BCP Team Selection](#bcp-team-selection) – p 117  
  - [Resource Requirements](#resource-requirements) – p 119  
  - [External Dependencies](#external-dependencies) – p 120  
- [Business Impact Analysis](#business-impact-analysis) – p 121  
  - [Identifying Priorities](#identifying-priorities) – p 122  
  - [Risk Identification](#risk-identification) – p 123  
  - [Likelihood Assessment](#likelihood-assessment) – p 125  
  - [Impact Analysis](#impact-analysis) – p 126  
  - [Resource Prioritization](#resource-prioritization) – p 128  
- [Continuity Planning](#continuity-planning) – p 128  
  - [Strategy Development](#strategy-development) – p 129  
  - [Provisions and Processes](#provisions-and-processes) – p 129  
- [Plan Approval and Implementation](#plan-approval-and-implementation) – p 131  
  - [Plan Approval](#plan-approval) – p 131  
  - [Plan Implementation](#plan-implementation) – p 132  
  - [Communication, Training and Education](#communication-training-and-education) – p 132  
  - [BCP Documentation](#bcp-documentation) – p 132  
- [Summary](#summary) – p 136  

## Planning for Business Continuity  

Business Continuity Planning (BCP) ensures an organization can **maintain or quickly resume** mission-critical operations when disruptive events occur.  
- 🔑 **Purpose:** Safeguard people first, then processes and technology.  
- **Scope:** Addresses *all* hazards—natural, technological, or human-made—and aims to minimize operational, financial, regulatory, and reputational impacts.  
- **Perspective vs. DRP:**  
  - BCP = strategic, *keep the business running*.  
  - DRP = tactical, *restore IT services*.
 
| **Phase** | **Purpose / Focus** | **Core Sub-Tasks** | **Key Deliverables / Artifacts** |
|-----------|--------------------|--------------------|----------------------------------|
| **1. Project Scope & Planning** | Define boundaries, stakeholders, and resources for BCP program. | • Organizational Review  <br>• BCP Team Selection  <br>• Resource Requirements  <br>• External Dependencies | • BCP Charter & Scope Statement  <br>• Stakeholder / Department Register  <br>• Resource Inventory & Budget  <br>• Vendor & Regulatory Dependency List |
| **2. Business Impact Analysis (BIA)** | Identify critical functions, quantify/qualify risks, and set recovery objectives. | • Identifying Priorities  <br>• Risk Identification  <br>• Likelihood Assessment (ARO)  <br>• Impact Analysis (EF, SLE, ALE)  <br>• Resource Prioritization | • Prioritized Process List  <br>• MTD / RTO / RPO Metrics  <br>• Quantitative Risk Register  <br>• Qualitative Impact Narrative  <br>• Recovery Objective Baselines |
| **3. Continuity Planning** | Design controls to keep critical functions running within objectives. | • Strategy Development (accept / mitigate / transfer / avoid)  <br>• Provisions & Processes for People, Facilities, Infrastructure | • Continuity of Operations Plan (COOP)  <br>• Hardening & Redundancy Design Docs  <br>• Alternate Site & Cloud-Failover Contracts  <br>• Personnel Safety & Logistics Plans |
| **4. Plan Approval & Implementation** | Obtain leadership endorsement, roll out controls, train staff, and maintain the plan. | • Plan Approval (executive sign-off)  <br>• Plan Implementation Schedule  <br>• Communication, Training & Education  <br>• BCP Documentation & Version Control | • CEO/Board Approval Letter  <br>• Implementation & Testing Calendar  <br>• Training Records & Exercise Reports  <br>• Living BCP Document Repository  <br>• Maintenance & Review Log |
 

| BCP Characteristic | Exam-Ready Definition |
|--------------------|-----------------------|
| **Mission-Essential Function** | A service whose loss jeopardizes the organization’s survival or legal/contractual obligations. |
| **Maximum Tolerable Downtime (MTD)** | Longest outage that can be endured before unacceptable consequences occur. |
| **Recovery Time Objective (RTO)** | Target time to restore a service after interruption—must fit within MTD. |
| **Recovery Point Objective (RPO)** | Maximum tolerable data loss, expressed as time between last good backup and interruption. |

> 📌 *Exam Tip:* Know how BCP metrics (MTD, RTO, RPO) inter-relate and that **life safety** outranks everything else.

## Project Scope and Planning  

Establishes the *foundation* for a resilient BCP by defining who is involved, what must be protected, and which resources are required.

### Organizational Review  

Identify every stakeholder, location, and dependency that influences continuity.  
- Map **lines of business, support services, and leadership.**  
- Consider headquarters, branch offices, data centers, and **cloud or managed-service footprints**.  
- Document critical processes, inter-dependencies, and regulatory drivers.

### BCP Team Selection  

A cross-functional team brings the expertise, authority, and perspective necessary to craft a workable plan.  
| Role | Typical Representative | Core Responsibility |
|------|-----------------------|---------------------|
| Executive Sponsor | C-Suite / VP | Priorities, funding, approval authority |
| BCP Program Manager | BC/DR lead or senior security engineer | Coordinates the entire effort |
| Operations Leads | Department managers | Define mission-essential functions |
| IT & Cybersecurity SMEs | System/network admins, security engineers | Outline technical safeguards and recovery steps |
| Facilities & Physical Security | Security director, building manager | Life-safety, site access, utilities |
| HR & Legal | HR director, general counsel | Staffing policies, legal/regulatory compliance |
| PR/Communications | Communications director | Stakeholder messaging during a crisis |

**Success factors:**  
- Diverse yet collaborative membership.  
- Explicit management mandate and decision-making authority.  
- Regular training and succession planning for key roles.  

### 🧑‍💼 Senior Management and Business Continuity Planning (BCP)

#### 🔹 Role of Senior Management in BCP

| Key Responsibility             | Description                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| Set Priorities                | Define what services and operations are most critical for continuity       |
| Allocate Resources            | Provide necessary staffing and budget for BCP activities                   |
| Arbitrate Criticality         | Make final decisions on disputes regarding the importance of services      |
| Provide Visible Support       | Show active and visible participation to legitimize the effort             |
| Meet Legal and Regulatory Duty| May be held **personally liable** if continuity planning is neglected       |
| Fulfill Fiduciary Duty        | Required to ensure adequate BCP is in place to protect shareholder interests|

#### 🔹 Key Takeaways from Case Study

> A senior executive asked, “Is there anything you need from me?”  
> The answer: “Yes—your **active participation**.”

##### Actions Taken by the Executive:
- Sent organization-wide email endorsing BCP initiative
- Participated in high-level planning sessions
- Spoke in a company town hall supporting the effort

✅ Result: **Increased engagement and organizational buy-in**

#### 🔹 Why Executive Involvement Matters

- **Sets the Tone from the Top**: Encourages other departments to take BCP seriously  
- **Prioritizes Planning over Day-to-Day Operations**  
- **Supports Regulatory Compliance**: e.g., SOX holds executives accountable  
- **Builds Trust**: Demonstrates to stakeholders that the organization is resilient

#### 📝 CISSP Exam Tips

- Expect questions on the **importance of executive sponsorship**
- Understand how **visible support impacts BCP success**
- Be aware of **legal and fiduciary responsibilities** linked to business continuity

### Resource Requirements  

Resources must be sized for **three distinct phases**:

| BCP Phase | People | Technology | Financial |
|-----------|--------|------------|-----------|
| **Development** | Project team hours, workshops | Project mgmt. tools, documentation platforms | Budget for consulting & assessment |
| **Testing / Training / Maintenance** | Exercise facilitators, trainees | Lab gear, staging servers, tabletop assets | Travel, exercise materials |
| **Implementation (Crisis Mode)** | All-hands on-deck, 24×7 shifts | Alternate sites, redundant links, spare hardware | Emergency procurement, overtime pay |

> 🔧 **Plan for labor**—personnel costs often dwarf hardware/software expenses.

### External Dependancies  

Even the strongest internal controls fail if external partners cannot deliver.

## Business Impact Analysis  

A Business Impact Analysis (BIA) pinpoints the **business processes & resources** essential for survival, quantifies/qualifies risks to them, and produces data that guides how continuity resources are allocated.

### Identifying Priorities  

1. **List mission-critical functions** (order processing, patient care, trading floor, etc.).  
2. Assign each a **Maximum Tolerable Downtime (MTD/MTO)**—the longest outage that will not cause irreparable harm.  
3. Determine a realistic **Recovery Time Objective (RTO)** for each function and a **Recovery Point Objective (RPO)** for its data.  
4. Capture **Asset Value (AV)** for quantitative analysis and note qualitative factors (reputation, compliance, life safety).  

| Metric | What It Describes | Exam Hint |
|--------|-------------------|-----------|
| **MTD** | “Can’t-be-down-longer-than” threshold | Always ≥ RTO |
| **RTO** | Time to restore the function | Must fit inside MTD |
| **RPO** | Acceptable data loss window | Drives backup cadence |
| **AV** | Monetary value of the asset/process | Basis for SLE |

### Risk Identification  

Catalog threats to prioritized functions—*no likelihood yet, just possibilities*.  
- **Natural:** hurricanes, earthquakes, pandemics, wildfire, floods.  
- **Person-made:** cyber-attacks, terrorism, vandalism, utility failure, economic crisis.  
- Use interviews, historical data, regulatory lists, and brainstorming to avoid blind spots.

### Likelihood Assessment  

Translate each threat into an **Annualized Rate of Occurrence (ARO)**.  
- Data sources: internal incident logs, insurance actuarial tables, government hazard maps, SME judgment.  
- Example: a region with a “1-in-25-year” flood risk ⇒ ARO = 0.04.

### Impact Analysis  

#### Quantitative (🔢 Hard Numbers)  

| Metric | Formula | Meaning |
|--------|---------|---------|
| **Exposure Factor (EF)** | % of AV lost | Severity of a single event |
| **Single Loss Expectancy (SLE)** | `SLE = AV × EF` | Cost of one event |
| **Annualized Loss Expectancy (ALE)** | `ALE = SLE × ARO` | Yearly averaged loss |

> *Example:* AV $500 k building, EF 70 % (fire), ARO 0.03 ⇒ SLE $350 k, ALE $10 .5 k.

#### Qualitative (🧭 Intangibles)  
Assess non-monetary impacts such as:  
- Brand/reputation damage  
- Legal/regulatory penalties  
- Life-safety & ethical duties  
- Workforce morale & retention  

Combine workshop scoring (High/Med/Low) with narratives to capture context numeric models miss.

### Resource Prioritization  

1. **Sort risks by ALE** (highest to lowest) to get an initial quantitative ranking.  
2. Overlay **qualitative concerns** to raise or lower items where money isn’t the whole story (e.g., life-safety threats, cornerstone clients, societal obligations).  
3. Allocate continuity dollars, staff, and time from the top down until the budget (or risk tolerance) is exhausted.  

| Step | Output |
|------|--------|
| **1. ALE list** | Data-driven ordering of risks |
| **2. Qualitative overlay** | Adjusted priorities reflecting reputation, ethics, compliance |
| **3. Final list → spend plan** | Funding, controls, run-books mapped to highest-priority risks |

#### Quantitative vs Qualitative – Quick Comparison  

| Aspect | Quantitative | Qualitative |
|--------|--------------|-------------|
| **Basis** | Dollar values, formulas | Subjective ratings, narratives |
| **Strength** | Objective; easy to rank | Captures brand & ethical stakes |
| **Weakness** | Misses intangibles | Can be biased |
| **Best Used** | Budget justification | Board discussions, reputation-heavy scenarios |

### Key Takeaways 🎯  

- **BIA is both math & judgment**—embrace *both* viewpoints.  
- Always ensure **RTO < MTD** and backup frequency meets **RPO**.  
- Understand and memorize **EF, SLE, ARO, ALE** formulas for exam problems.  
- Final prioritization marries numbers with common sense and corporate values.  

## Continuity Planning  

After scope definition and the BIA, **Continuity Planning** designs the controls that keep critical functions running during an incident.  
- 🔑 **Output:** a Continuity of Operations Plan (COOP) covering the first minutes through ~30 days post-event.  

### Strategy Development  

1. **Accept vs. Mitigate:** Compare each risk’s **cost of mitigation** to its ALE & qualitative impact.  
2. **Risk Triage:** Eliminate negligible threats (e.g., blizzards in Egypt), commit resources where MTD/RTO would be breached.  
3. **Cost–Benefit Rule:** Only mitigate when the cost of controls < expected annual loss or qualitative harm.  
4. **Resource Allocation:** Map budget, people, and time to the chosen mitigation set.  

| Decision Path | Trigger | Result |
|---------------|---------|--------|
| **Accept** | Risk < risk appetite | Document rationale & monitor |
| **Transfer** | Insurance or contract viable | Purchase policy / SLA |
| **Mitigate** | Cost-effective controls | Proceed to provisions & processes |
| **Avoid** | Activity optional & high risk | Discontinue or redesign |

### Provisions and Processes  

Continuity controls fall into **three asset domains**:

#### People 👥  
- Life-safety protocols, evacuation & shelter-in-place drills.  
- Rotating **food / water stockpiles** for on-site staff.  
- Cross-training & backups for every BCP role.

#### Buildings & Facilities 🏢  
| Control Type | Examples | Notes |
|--------------|----------|-------|
| **Hardening** | Roof repair, reinforced shutters, fire-rated walls | Preferred when feasible & affordable |
| **Alternate Sites** | Hot, warm, cold, mobile, cloud workspace | Activated when primary breaches MTD |

#### Infrastructure 🌐  
- **Hardening:** UPS, dual generators, clean-agent suppression, surge filters.  
- **Redundancy:** Multi-carrier WAN, cluster pairs, multi-region cloud, secondary logistics hubs.  
- **Cloud Vetting:** Vendor SOC 2/SOC 3, multi-AZ/region replication, failover playbooks.

## Plan Approval and Implementation  

Senior-executive endorsement transforms the document into an enterprise mandate.

### Plan Approval  

- Obtain signature from CEO/President (best) or equivalent.  
- Approval letter doubles as **Statement of Importance & Responsibility**.

### Plan Implementation  

1. **Build Schedule:** Sequenced rollout of hardening projects, alt-site contracts, training.  
2. **Maintenance Program:** Quarterly review; update for org or threat changes.  
3. **Metrics Tracking:** Dashboards for RTO/RPO attainment, exercise scores.

### Communication, Training and Education  

| Audience | Format | Frequency | Objective |
|----------|--------|-----------|-----------|
| **All Staff** | Awareness brief / intranet page | Annual & onboarding | Confidence & high-level roles |
| **BCP Role Holders** | Hands-on workshops, tabletops | Semi-annual | Task proficiency |
| **Alternates** | Shadow sessions | Same as primary | Redundancy |

> 📌 **Backup for every role**—no single point of human failure.

### BCP Documentation  

Essential elements (*keep version-controlled & distributed securely*):  

1. **Continuity Goals** – explicit uptime/downtime targets.  
2. **Statements** – Importance, Priorities, Responsibility, Urgency.  
3. **Risk Assessment Recap** – AV, EF, ARO, SLE, ALE + qualitative discussion.  
4. **Risk Acceptance/Mitigation Rationale** – signed by risk owners.  
5. **Vital Records Program** – inventory, storage, backup cadence.  
6. **Emergency Response Guidelines** – who calls whom, in what order, with checklists.  
7. **Maintenance & Version Control** – review cadence, change log.  
8. **Testing & Exercise Plan** – schedule & type (walk-through, tabletop, parallel, full-interruption).

### Quick Review 🎯  

- **Strategy Development** picks which risks to treat based on MTD/RTO and cost-benefit.  
- **Provisions & Processes** cover **people, facilities, infrastructure** with hardening or redundancy.  
- **Executive sign-off** gives authority; implementation = schedule + maintenance.  
- **Training & Documentation** turn theory into muscle memory and legal proof.  
- Keep the BCP a **living document**—continuous updates, version control, and exercises guarantee relevance.

*Master these phases—CISSP exam questions often ask for the “next best step” once strategy is set or the plan is approved.* 🔥


------------------
# 📘 CISSP Quantitative Risk Analysis ノート

---

## 🔑 用語と定義

| 略語 | 用語 | 定義 |
|------|------|------|
| **AV** | Asset Value（資産価値） | 保護対象資産の金銭的価値（例：建物、設備、サーバなど） |
| **EF** | Exposure Factor（影響係数） | 1回のインシデントでどれだけ損失を受けるかの割合（%） |
| **SLE** | Single Loss Expectancy（単一損失期待値） | 1回の事故で被る金銭的損失 |
| **ARO** | Annualized Rate of Occurrence（年間発生率） | そのイベントが1年間に発生する予測頻度 |
| **ALE** | Annualized Loss Expectancy（年間損失期待値） | 年間で予測される損失額（SLE × ARO） |

---

## 📐 計算式

```
SLE = AV × EF
ALE = SLE × ARO
```

---

## ✅ 計算例

**シナリオ：**  
- 資産価値（AV） = $200,000  
- 影響係数（EF） = 50%（0.5）  
- 年間発生率（ARO） = 0.2（年に20%の確率で発生）

**計算結果：**  
- SLE = $200,000 × 0.5 = $100,000  
- ALE = $100,000 × 0.2 = $20,000

---

## 🧪 練習問題

### Q1.  
あるデータセンターの資産価値は $500,000。火災が発生すると 40% の損失が予測される。このときの **SLE** は？

- A. $100,000  
- B. $200,000  
- C. $300,000  
- D. $400,000  

---

### Q2.  
サイバー攻撃の年間発生率（ARO）が 2、SLE が $150,000 の場合、**ALE** はいくらか？

- A. $75,000  
- B. $300,000  
- C. $150,000  
- D. $600,000  

---

### Q3.  
あなたの施設は $3,000,000 の価値がある。90% が建物、10% が土地。雪崩で建物が破壊されるが土地は影響を受けない場合、**SLE** は？

- A. $3,000,000  
- B. $2,700,000  
- C. $300,000  
- D. $1,500,000  

---

### Q4.  
**Exposure Factor（EF）** の定義として正しいものはどれか？

- A. 年間にイベントが発生する確率  
- B. 1回のイベントで発生する回復コスト  
- C. 単一イベントで失われる資産価値の割合  
- D. 年間の損失予測額  

---

## 📎 正解と解説

### ✅ Q1 正解：B. $200,000  
**解説：**  
SLE = $500,000 × 0.4 = **$200,000**

---

### ✅ Q2 正解：B. $300,000  
**解説：**  
ALE = $150,000 × 2 = **$300,000**

---

### ✅ Q3 正解：B. $2,700,000  
**解説：**  
SLE = $3,000,000 × 0.9 = **$2,700,000**（土地は影響を受けないため除外）

---

### ✅ Q4 正解：C. 単一イベントで失われる資産価値の割合  
**解説：**  
EFは影響を受ける割合を示す指標であり、例：60%損害＝EF 0.6

---

## 📝 まとめ

| 指標 | 説明 | 単位例 |
|------|------|---------|
| AV | 資産の金銭的価値 | $100,000 |
| EF | 損失割合 | 0.4（＝40%） |
| SLE | 単一インシデントの損失額 | $40,000 |
| ARO | 年間発生頻度 | 1.5回／年 |
| ALE | 年間総損失見積額 | $60,000 |

---

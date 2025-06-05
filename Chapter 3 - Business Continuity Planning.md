# Chapter 3 - Business Continuity Planning

1. Planning for Business Continuity
2. Project Scope and Planning
3. Business Impact Analysis
4. Continuity Planning
5. Plan Approval and Implementation
6. Summary
---

## 3.1  Planning for Business Continuity
Business Continuity Planning (BCP) is the **umbrella discipline** that ensures an organization can **sustain mission-critical operations** during, and quickly recover after, a disruptive event.

* **BCP vs DRP** – DRP (Disaster Recovery Planning) is a technical subset (systems & data), whereas BCP covers people, processes, and facilities.
* **4 main elements**:<br>
(1) Project scope and planning<br>
(2) Business impact analysis<br>
(3) Continuity planning<br>
(4) Plan approval and implementation<br>
* **Objectives:** Safeguard life/safety, minimize financial loss, maintain customer confidence, meet legal/regulatory mandates (ISO 22301, NIST SP 800-34, FFIEC).  
* **Governance:** Senior management sponsorship, board‐level policy, risk appetite definition.  
* **Key Terms:** Resilience, redundancy, recovery, survivability, crisis management.

---

## 3.2  Project Scope and Planning  
Establish a formal, well-funded project—**charter + timeline + owners**—before analysis or solutions begin.

### 3.2.1  Organizational Review
* **Mission-critical functions**  
* Lines of business, stakeholders, regulatory landscape  
* Dependencies: internal, external, upstream/downstream processes  

### 3.2.2  BCP Team Selection
* **Executive sponsor** (provides authority & budget)  
* **BCP coordinator / project manager**  
* Representatives: IT, HR, Legal, Facilities, Comms/PR, Finance, Security, third-party advisors  
* RACI matrix for accountability  

### 3.2.3  Resource Requirements
* Budget (CAPEX/OPEX)  
* Personnel availability, subject-matter experts  
* Tools: BIA software, risk-analysis platforms, secure documentation system  
* Training funds & exercise logistics  

### 3.2.4  External Dependencies
* Cloud & SaaS/PaaS/IaaS providers  
* Critical suppliers & supply-chain pathways  
* Public utilities, telecom carriers, emergency services  
* Contractual SLAs, mutual-aid or reciprocal-site agreements  

---

## 3.3  Business Impact Analysis (BIA)  
Objective: **Quantify the operational and financial impact** of disruptions to set recovery targets.

### 3.3.1  Identifying Priorities
* **Process mapping** – document workflows, owner, inputs/outputs  
* **Criticality rating** – essential, important, non-essential  

### 3.3.2  Risk Identification
* Threat catalog: natural (flood, hurricane), technological (system failure, cyber-attack), human (sabotage, strike)  
* Vulnerability analysis, single points of failure  

### 3.3.3  Likelihood Assessment
* Qualitative (high/med/low) or quantitative (annual rate of occurrence – **ARO**)  
* Historical data, industry benchmarks, insurance actuarials  

### 3.3.4  Impact Analysis
* **Maximum Tolerable Downtime (MTD/MTO)**  
* **Recovery Time Objective (RTO)** – target restoration time  
* **Recovery Point Objective (RPO)** – maximum tolerable data loss  
* **Work Recovery Time (WRT)**, **Service Delivery Objective (SDO)**  
* Financial loss, legal penalties, safety impact, reputational damage  

### 3.3.5  Resource Prioritization
* Ranked list of assets/processes by criticality  
* Dependency matrix (people, IT, facilities, vendors)  
* Cost–benefit for potential controls/strategies  

---

## 3.4  Continuity Planning

### 3.4.1  Strategy Development
* **People:** cross-training, succession, remote work, shelter-in-place  
* **Facilities:** hot/warm/cold sites, reciprocal agreements, mobile sites, colo/cloud DRaaS  
* **Technology:** clustering, fail-over, virtualization, IaC, backups (full, incremental, diff), **CDP**  
* **Data:** on-site vs off-site vaulting, synchronous/asynchronous replication, immutable backups  
* **Supply chain:** multi-sourcing, alternate suppliers, inventory buffers  
* **Risk treatment:** avoidance, transference (insurance), mitigation, acceptance  

### 3.4.2  Provisions and Processes
* Emergency response procedures (life safety first)  
* Escalation & declaration criteria  
* Crisis communications – internal, external, media, regulators  
* Work-arounds & manual procedures  
* Alternate communications (VoIP, SAT phone, radio)  
* Vital records protection; documentation, forms, checklists  

---

## 3.5  Plan Approval and Implementation

### 3.5.1  Plan Approval
* Executive sign-off, legal/compliance review, budget commitment  
* Alignment with enterprise risk management (ERM) strategy  

### 3.5.2  Plan Implementation
* Publish controlled copies (paper & secure digital)  
* Integrate with change-management & CMDB  
* Pre-position equipment, seed data to alternates, stage emergency kits  

### 3.5.3  Communication, Training and Education
* Awareness sessions vs role-based training  
* Orientation drills for new hires, periodic refresher courses  
* Specialized instruction for recovery-team members  
* Exercise schedule embedded in policy  

### 3.5.4  BCP Documentation
* Plan sections: Introduction, Roles/Contacts, Activation, Response, Recovery, Restoration, Appendices  
* Version control, audit trail, confidentiality classification  
* Secure storage (on-prem fire-safe + off-site/cloud)

---

## 3.6  Summary
Business Continuity Planning **protects mission-critical operations** by integrating risk assessment, impact analysis, strategic safeguards, and ongoing governance. A **mature BCP** earns executive support, is rooted in a thorough BIA, specifies clear RTO/RPO targets, and is continually improved through testing, training, and periodic reviews. Mastery of these concepts—and the associated metrics, roles, and frameworks—is essential for the CISSP exam and, more importantly, for building resilient organizations.


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

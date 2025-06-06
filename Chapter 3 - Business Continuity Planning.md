# Chapter 3 - Business Continuity Planning

- [Planning for Business Continuity]()
- [Project Scope and Planning]()
  - [Organizational Review]()
  - [BCP Team Selection]()
  - [Resource Requirements]()
  - [External Dependancies]()
- [Business Impact Analysis]()
  - [Identifying Priorities]()
  - [Risk Identification]()
  - [Likelihood Assessment]()
  - [Impact Analysis]()
  - [Resource Prioritization]()
- [Continuity Planning]()
  - [Strategy Development]()
  - [Provisions and Processes]()
- [Plan Approval and Implementation]()
  - [Plan Approval]()
  - [Plan Implementation]()
  - [Communication, Training and Education]()
  - [BCP Documentation]()
- [Summary]()

## Planning for Business Continuity  
**Core idea:**  BCP keeps critical business services running (or quickly restored) despite disruptive events.  

**Key take-aways**  
- Objective = **life safety first, business survival second, profitability third**.  
- Align BCP effort with **risk appetite** & regulatory uptime mandates.  
- Executive sponsorship + cross-functional participation is mandatory.

---

## Project Scope and Planning  

### Organizational Review  
- Inventory **critical functions, dependencies, legal obligations**.  
- Perform gap analysis of existing DR/BC capabilities.

### BCP Team Selection  
- Multidisciplinary: exec sponsor, BC manager, IT, facilities, HR, comms, legal.  
- Define **RACI** and escalation chains.

### Resource Requirements  
- Budget, manpower, tooling (e.g., BCM software, alternate-site contracts).  
- Time commitments from business units.

### External Dependencies  
- Third-party services, utilities, cloud providers, supply-chain partners.  
- Ensure contracts include **BC/DR clauses** & right-to-audit.

---

## Business Impact Analysis  

### Identifying Priorities  
- Rank processes by **criticality, revenue impact, life-safety impact**.  
- Define **Maximum Tolerable Downtime (MTD)** for each process.

### Risk Identification  
- List threats: natural, human, environmental, technical.  
- Include single-points-of-failure & supply-chain risks.

### Likelihood Assessment  
- Qualitative or quantitative frequency estimates (e.g., historic data, actuarial tables).

### Impact Analysis  
- Financial (lost revenue, penalties), operational, reputational.  
- Determine **Recovery Time Objective (RTO)** and **Recovery Point Objective (RPO)**.

### Resource Prioritization  
- Map critical processes to required people, facilities, IT, vendors.  
- Create prioritized restoration sequence.

---

## Continuity Planning  

### Strategy Development  
- Choose **recovery options**: hot/warm/cold site, active-active, cloud failover, manual workaround.  
- Cost–benefit aligned with RTO/RPO.

### Provisions and Processes  
- Draft step-by-step **response & recovery playbooks**.  
- Include alternate communications, vendor contacts, data-restore, manual ops, public-relations scripts.  
- Integrate life-safety procedures (evacuation, shelter-in-place).

---

## Plan Approval and Implementation  

### Plan Approval  
- Senior management must **review, fund, and sign** the BCP.  
- Confers legal authority and budget.

### Plan Implementation  
- Roll-out controls (redundant links, backup schedules, site contracts).  
- Populate call trees, emergency kits, runbooks.

### Communication, Training and Education  
- Awareness for all staff; role-based BC training; exec tabletop drills.  
- Ensure 24×7 accessibility of plan (hard copy + offline digital).

### BCP Documentation  
- Version-controlled BC/DR manual, RTO/RPO matrices, contact lists, test results, maintenance logs.

---

## Summary  
A solid BCP life-cycle = **Scope → BIA → Strategy → Plan → Approve → Implement → Train → Test → Maintain**.  
Master RTO/RPO/MTD, alternate-site types, and the need for executive buy-in and continuous improvement—recurring CISSP exam themes.


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

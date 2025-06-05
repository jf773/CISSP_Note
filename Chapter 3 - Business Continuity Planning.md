# Chapter 3 - Business Continuity Planning

## Concepts
### Business Continuity Planning
**Definition:** Business continuity planning **ensures a business keeps running during adversity**, such as system failures, natural disasters, or human-made incidents.

**Focus:** The **primary goal** is to maintain operations, supporting the security objective of **availability**.

**Process:** The BCP process has four main steps:
■■ **Project scope and planning**
■■ **Business impact analysis**
■■ **Continuity planning**
■■ **Approval and implementation**

**Scope Definition:** Teams should define the scope upfront, including covered business activities, systems, and controls.

**Business Impact Assessment (BIA):** A tool used to **identify mission-essential functions, critical IT systems, potential risks, and prioritize risks** based on expected loss.

**Control Selection:** Mitigate risks within acceptable expense limits, considering cost-effectiveness.

**Cloud-Centric Environment:** Collaboration between cloud service providers and customers to mitigate risks, such as replicating services across data centers.

**External Dependencies:** Include third-party vendors, supply chain partners, and critical infrastructure elements in the continuity plan to anticipate potential disruptions.

### Business Continuity Controls
**Redundancy:** Ensuring systems are redundant so that a failure of a single component doesn't bring the entire system down.

**Single Point of Failure Analysis:** Identifying and removing single points of failure from systems.

**Example:** Replacing a single web server with a clustered farm of servers to ensure service continuity.

**High-Availability Firewalls:** Replacing a single firewall with a pair of high-availability firewalls to ensure continuous service if one fails.

**Network Connections:** Introducing redundancy in internal and external network connections to maintain service if one link fails.

**Comprehensive Risk Consideration:** Considering other risks such as vendor bankruptcy, utility service failures, and computing/storage capacity issues.

**Personnel Succession Planning:** Identifying essential team members and potential successors to ensure continuity of operations when someone leaves the organization.

### High Availability and Fault Tolerance
**High Availability (HA)**

**Definition:** Uses multiple systems to protect against failures.

**Example:** A cluster of web servers that can continue to operate even if a single server fails.

**Geographic Dispersal:** Placing systems in different locations to protect against facility damage.

**Fault Tolerance (FT)**

**Definition:** Helps protect a single system from failing by making it resilient to technical failures.

**Example:** Dual power supplies in servers to ensure continuous operation if one fails.

**Load Balancing**

**Definition:** Uses multiple systems to spread the burden of providing a service.

**Difference from HA:** While both use similar technologies, load balancing focuses on scalability, whereas HA focuses on redundancy.

**Common Points of Failure**

**Power Supply:** Dual power supplies and uninterruptible power supplies (UPSs) can mitigate this risk.

**Storage Media:** RAID technologies like mirroring and striping with parity protect against disk failures.

**Networking:** Redundancy in network paths and NIC teaming can prevent network failures.

**RAID Technologies (= Fault Tolerance Technology)**

**RAID Level 1 (Mirroring):** Two disks with identical contents; if one fails, the other continues operation.

**RAID Level 5 (Striping with Parity):** Data spread across multiple disks with parity blocks; can regenerate data if one disk fails.

**Note:** RAID level 5 requires a minimum of 3 disk drives.

**Network Redundancy**

**NIC Teaming:** Using multiple network interface cards in critical servers.

**Multi-Path Approaches:** Creating redundancy in network connections to ensure continuous access to storage.

**Diversity in Technologies**

**Vendor Diversity:** Using diverse technologies from different vendors to avoid simultaneous failures.

**Cryptography and Security Controls:** Diversifying these elements to enhance resilience.

---------------------------------
## Test Questions
---------------------------------

**Question 1:** What is the primary objective of business continuity planning?

A) To ensure data confidentiality

B) To maintain business operations during adverse events

C) To enhance data integrity

D) To improve network security

**Question 2:** Which tool is used to identify mission-essential functions and trace them to critical IT systems in business continuity planning?

A) Risk assessment

B) Business impact assessment (BIA)

C) Security audit

D) Vulnerability scan

**Question 3:** In a cloud-centric environment, who is responsible for mitigating the risk of a hurricane damaging a data center?

A) The cloud service provider only

B) The customer only

C) Both the cloud service provider and the customer

D) The government

**Question 4:** Which of the following is a critical method for ensuring system availability in business continuity planning?

A) Implementing a single point of failure

B) Ensuring redundancy

C) Using a single firewall

D) Relying on a single network connection


**Question 5:** What is the purpose of a single point of failure analysis in business continuity planning?

A) To identify and remove single points of failure from systems

B) To create a single point of failure in systems

C) To ensure that only one component is responsible for system failure

D) To increase the number of single points of failure

**Question 6:** Which of the following is NOT a potential risk that should be considered in business continuity planning?

A) Sudden bankruptcy of a key vendor

B) Utility service failures

C) High-availability firewalls

D) Inability to provide computing or storage capacity

**Question 7:** Why is personnel succession planning important in business continuity planning?

A) To identify single points of failure in hardware

B) To ensure that there are backups for critical team members

C) To create redundancy in network connections

D) To implement high-availability firewalls

**Question 8:** Which of the following best describes high availability (HA)?

A) Using multiple systems to protect against failures.

B) Making a single system resilient in the face of technical failures.

C) Spreading the burden of providing a service across multiple systems.

D) Ensuring continuous access to storage.

**Question 9:** What is the primary goal of fault tolerance (FT)?

A) To provide a scalable computing environment.

B) To protect a single system from failing in the first place.

C) To distribute network traffic evenly across multiple systems.

D) To ensure continuous access to storage.


**Question 10:** Which RAID level is known as disk mirroring?

A) RAID 0

B) RAID 1

C) RAID 5

D) RAID 10


**Question 11:** What is NIC teaming?

A) Using multiple power supplies in a server.

B) Using multiple network interface cards in critical servers.

C) Using multiple disks for data storage.

D) Using multiple firewalls for redundancy.



---------------------------------
## Answers and Explanations
---------------------------------

**Answer 1:** B) To maintain business operations during adverse events

Explanation: The primary objective of business continuity planning is to keep business operations running during adverse events, ensuring the availability of critical functions.

**Answer 2:** B) Business impact assessment (BIA)

Explanation: A Business Impact Assessment (BIA) helps identify mission-essential functions and trace them to critical IT systems, which is crucial for prioritizing risks and selecting appropriate controls.

**Answer 3:** C) Both the cloud service provider and the customer

Explanation: In a cloud-centric environment, business continuity planning is a collaboration between the cloud service provider and the customer. Both parties play a role in mitigating risks, such as replicating services across data centers and implementing flood prevention systems.

**Answer 4:** B) Ensuring redundancy

Explanation: Ensuring redundancy means designing systems so that the failure of a single component does not bring down the entire system. This is crucial for maintaining system availability.

**Answer 5:** A) To identify and remove single points of failure from systems

Explanation: The single point of failure analysis helps security professionals identify and remove components that could cause the entire system to fail if they malfunction.

**Answer 6:** C) High-availability firewalls

Explanation: High-availability firewalls are a solution to mitigate risks, not a risk themselves. Business continuity planning should consider risks like vendor bankruptcy, utility failures, and capacity issues.

**Answer 7:** B) To ensure that there are backups for critical team members

Explanation: Personnel succession planning ensures that there are trained and prepared successors for critical team members, maintaining continuity in operations if someone leaves the organization.

**Answer 8:** A) Using multiple systems to protect against failures.

Explanation: High availability (HA) involves using multiple systems to ensure that if one system fails, others can continue to operate, thus protecting against failures.

**Answer 9:** B) To protect a single system from failing in the first place.

Explanation: Fault tolerance (FT) aims to make a single system resilient to technical failures, preventing it from failing in the first place.

**Answer 10:** B) RAID 1

Explanation: RAID 1, also known as disk mirroring, involves having two disks with identical contents. If one disk fails, the system can switch to the backup disk without interruption.

**Answer 11:** B) Using multiple network interface cards in critical servers.

Explanation: NIC teaming involves using two or more network interface cards in critical servers to ensure network redundancy and continuous operation if one card fails.

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

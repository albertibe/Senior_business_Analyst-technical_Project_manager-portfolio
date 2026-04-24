# Case Study 03 — Executive Analytics Platform
## University of Lethbridge | Senior Business Analyst (via ECG)

---

## Organization Profile

**Organization:** University of Lethbridge  
**Sector:** Higher Education  
**Role:** Senior Business Analyst (Embedded via Expertedge Consulting Group)  
**Duration:** March 2022 – Present  
**Platform:** Microsoft Power BI, Azure Data Services  

---

## Executive Summary

Designed and deployed an enterprise Power BI analytics platform consolidating data from 10+ institutional systems for 5 senior leaders. Replaced a fragmented, manual weekly reporting process with a real-time, self-service executive dashboard suite — eliminating manual report production and accelerating institutional decision-making cycles.

---

## The Challenge

The University's senior leadership team was making critical decisions — budget allocation, enrollment strategy, workforce planning — using data that was:

- **7–10 days old** by the time it reached decision-makers (manual Excel compilation cycle)
- **Inconsistent** — different departments reported the same metric differently with no agreed definition
- **Labour-intensive** — 3 staff members spending 6+ combined hours per week on manual report compilation
- **Siloed** — no single view combining financial, HR, student, and operational data

The result was that leadership meetings were frequently delayed by data disputes, decisions were made on stale information, and the reporting staff had no capacity for analytical work.

---

## Approach

### Discovery (Weeks 1–4)
- Interviewed 5 senior leaders to understand their top 10 questions that data should answer
- Mapped current reporting landscape — identified 14 existing reports across 6 systems with overlapping and conflicting metrics
- Conducted data quality assessment across source systems
- Defined a common metrics glossary — 47 institutional metrics defined, agreed, and documented

### Design (Weeks 5–8)
- Designed star-schema data model consolidating HR, Finance, Student, and Operational data
- Created wireframe mockups for 3 dashboard modules — reviewed and approved by each senior leader
- Defined row-level security model ensuring each leader sees only data within their portfolio
- Documented data lineage from source system to dashboard metric for all 47 KPIs

### Build (Weeks 9–16)
- Built Power BI data model connecting 10+ source systems via Power Query and Azure Data Factory
- Developed 3 dashboard modules: Executive Overview, Financial Performance, and Workforce Analytics
- Implemented row-level security via Entra ID group membership
- Configured automated data refresh — dashboards updated every 4 hours during business hours

### Deployment and Adoption (Weeks 17–20)
- Conducted 1:1 training sessions with each of the 5 senior leaders
- Published dashboards to Power BI Service with mobile app access enabled
- Established data stewardship process for metric definition changes
- Documented all data sources, transformations, and metric definitions in a Data Dictionary

---

## Results

| Metric | Before | After | Improvement |
|---|---|---|---|
| Data freshness for leadership | 7–10 days old | 4-hour refresh cycle | **↓ 95%+ latency** |
| Weekly manual reporting effort | 6+ hours / week (3 staff) | <30 min / week (exception only) | **↓ 92%** |
| Metrics with agreed definitions | ~30% | 100% (47 defined) | **+70 percentage points** |
| Data sources consolidated | 14 separate reports / 6 systems | 1 platform / 3 dashboards | **Unified** |
| Leadership meeting preparation time | 2 hours per meeting | 15 minutes | **↓ 88%** |
| Data disputes in leadership meetings | Frequent (weekly) | Rare (<1/month) | **↓ ~90%** |

---

## Key Design Decisions

**Decision 1: Star schema over flat tables**
Early prototypes used flat query outputs that were slow and hard to maintain. Rebuilt as a proper star schema — fact tables for transactions, dimension tables for time, department, program, and person. Dashboard query performance improved by 8x.

**Decision 2: Metrics glossary before build**
Insisted on a signed metrics glossary before a single DAX measure was written. This prevented the most common Power BI failure mode — building dashboards where no one agrees what the numbers mean.

**Decision 3: Row-level security via Entra ID**
Rather than managing security within Power BI directly, linked RLS to existing Entra ID groups. When an executive changes role, their dashboard access updates automatically — no manual Power BI security management required.

**Decision 4: Mobile-first for senior leaders**
Senior leaders requested dashboard access on mobile. Designed all visuals for mobile layout first, then adapted for desktop — resulting in dashboards that work on both without separate development effort.

---

## Artifacts Produced

| Artifact | Description |
|---|---|
| Data Model Documentation | Star schema ERD with all table relationships and field definitions |
| Metrics Glossary | 47 institutional KPIs with agreed definitions, owners, and calculation logic |
| Data Lineage Map | Source-to-dashboard lineage for all metrics |
| Row-Level Security Design | Security model mapping Entra ID groups to dashboard permissions |
| Dashboard Wireframes | Approved mockups for all 3 dashboard modules |
| Data Refresh Runbook | IT runbook for maintaining data refresh and troubleshooting |
| User Training Guide | Step-by-step guide for senior leader dashboard users |

---

*Related: [Data Governance Portfolio](https://github.com/albertibe/data-governance-framework) — covers the governance framework applied to this initiative including data classification and access policies.*

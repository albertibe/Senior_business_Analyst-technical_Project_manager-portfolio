# Current State (As-Is) Process Map
## Manual Scholarship Application Process

> **Rendered automatically by GitHub.** This diagram uses Mermaid syntax and renders as a visual swimlane diagram on GitHub.

---

## Process Overview

**Process Name:** Scholarship Application — Current State (Manual)  
**Process Owner:** Director, Student Services  
**Analyst:** Albert Ibe, CBAP  
**Date Documented:** April 2026  
**Status:** As-Is (Pre-transformation)

**Key Metrics — Current State:**
- Average end-to-end processing time: **42 business days**
- Manual touchpoints: **18**
- Error rate (incomplete / incorrect applications): **24%**
- Staff effort per application: **3.5 hours**
- Weekly status enquiry calls handled manually: **40+**

---

## Swimlane Process Diagram

```mermaid
flowchart TD
    subgraph Applicant
        A1([Start]) --> A2[Download paper form\nfrom website]
        A2 --> A3[Complete form manually]
        A3 --> A4[Gather supporting documents\nin physical format]
        A4 --> A5[Mail or hand-deliver\napplication to office]
        A5 --> A6[Wait for acknowledgement\n— no visibility]
        A6 --> A7{Contacted by office?}
        A7 -- Missing docs --> A8[Re-submit missing\ndocuments]
        A8 --> A6
        A7 -- No contact --> A9[Call office for\nstatus update]
        A9 --> A6
        A7 -- Outcome received --> A10([End])
    end

    subgraph Student_Services_Staff
        B1[Receive physical application] --> B2[Log application manually\nin Excel spreadsheet]
        B2 --> B3{Application\ncomplete?}
        B3 -- Incomplete --> B4[Contact applicant\nby email or phone]
        B4 --> B1
        B3 -- Complete --> B5[Manually verify enrollment\nstatus in SIS — separate login]
        B5 --> B6[Calculate eligibility score\nmanually in Excel]
        B6 --> B7[Compile shortlist in Excel]
        B7 --> B8[Email package to\nReview Committee]
        B8 --> B9[Respond to status\nenquiry calls — 40+/week]
    end

    subgraph Review_Committee
        C1[Receive Excel package\nby email] --> C2[Review applications\nindependently]
        C2 --> C3[Email votes and comments\nback to coordinator]
        C3 --> C4[Coordinator manually\ncollates committee responses]
        C4 --> C5[Committee meeting\nto finalize decisions]
        C5 --> C6[Email decisions to\nStudent Services]
    end

    subgraph Finance
        D1[Receive award list\nby email] --> D2[Manually create\npayment records in ERP]
        D2 --> D3[Process payment\non next payment run]
        D3 --> D4[Email payment\nconfirmation to Student Services]
    end

    A5 --> B1
    B8 --> C1
    C6 --> B9
    B9 --> A10
    D4 --> A10
```

---

## Key Pain Points Identified

| # | Pain Point | Impact |
|---|---|---|
| 1 | No online submission — applicants must physically deliver documents | Excludes remote and international applicants; high friction |
| 2 | No applicant portal — zero visibility into application status | 40+ weekly status calls consuming 2 FTE hours/week |
| 3 | Manual enrollment verification — separate SIS login required | 20 min per application; high error risk |
| 4 | Manual scoring in Excel — no standardized formula enforcement | 24% error rate in eligibility scoring |
| 5 | Committee review by email — no audit trail or version control | Decisions not traceable; compliance risk |
| 6 | Manual ERP data entry for payments — double entry of award data | Rework risk; payment delays |
| 7 | No automated notifications — staff must manually contact applicants | Resource-intensive; inconsistent applicant experience |

---

*Next: See [future-state-process.md](future-state-process.md) for the To-Be process design.*

# Future State (To-Be) Process Map
## Automated Scholarship Application Process

> **Rendered automatically by GitHub.** This diagram uses Mermaid syntax and renders as a visual swimlane diagram on GitHub.

---

## Process Overview

**Process Name:** Scholarship Application — Future State (Automated)  
**Process Owner:** Director, Student Services  
**Analyst:** Albert Ibe, CBAP  
**Date Documented:** April 2026  
**Status:** To-Be (Post-transformation target)

**Key Metrics — Future State Targets:**
- Average end-to-end processing time: **10 business days** (↓ from 42)
- Manual touchpoints: **4** (↓ from 18)
- Error rate: **<3%** (↓ from 24%)
- Staff effort per application: **0.5 hours** (↓ from 3.5 hours)
- Weekly status enquiry calls: **<5** (↓ from 40+)

---

## Future State Swimlane Diagram

```mermaid
flowchart TD
    subgraph Applicant
        A1([Start]) --> A2[Login via SSO\nEntra ID credentials]
        A2 --> A3[Complete online application\nform with validation]
        A3 --> A4[Upload digital supporting\ndocuments]
        A4 --> A5[Submit application]
        A5 --> A6[Receive instant email\nconfirmation with reference number]
        A6 --> A7[Track status in\nself-service portal — real time]
        A7 --> A8{Decision\nreceived?}
        A8 -- Awarded --> A9[Receive award\nnotification email]
        A8 -- Not awarded --> A10[Receive outcome\nnotification email]
        A9 --> A11([End])
        A10 --> A11
    end

    subgraph Scholarship_System_Automated
        S1[Receive application] --> S2[Validate completeness\nautomatically]
        S2 --> S3{Complete?}
        S3 -- Incomplete --> S4[Auto-email applicant\nwith specific missing items]
        S4 --> S1
        S3 -- Complete --> S5[Auto-verify enrollment\nvia SIS API integration]
        S5 --> S6[Auto-calculate\neligibility score]
        S6 --> S7[Route to committee\nreview queue]
        S7 --> S8[Notify committee\nmembers automatically]
        S8 --> S9[Collect committee\ndecisions in system]
        S9 --> S10{All decisions\ncollected?}
        S10 -- No --> S8
        S10 -- Yes --> S11[Auto-generate\naward list]
        S11 --> S12[Trigger payment\nvia Finance API]
        S12 --> S13[Auto-notify\napplicants of outcome]
        S13 --> A9
    end

    subgraph Review_Committee
        C1[Receive notification\nwith secure portal link] --> C2[Review applications\nin system — all in one place]
        C2 --> C3[Record decision and\ncomments in system]
        C3 --> C4{All applications\nreviewed?}
        C4 -- No --> C2
        C4 -- Yes --> C5[Chair confirms\nfinal award list in system]
    end

    subgraph Finance_System_Automated
        F1[Receive award trigger\nvia API] --> F2[Auto-create payment\nrecords in ERP]
        F2 --> F3[Process on next\npayment run]
        F3 --> F4[Auto-send payment\nconfirmation]
    end

    subgraph Student_Services_Staff
        M1[Monitor dashboard\nfor exceptions only] --> M2{Exception\nflagged?}
        M2 -- Yes --> M3[Review and\nresolve exception]
        M3 --> M1
        M2 -- No --> M4[Generate management\nreports as needed]
    end

    A5 --> S1
    S7 --> C1
    C5 --> S11
    S12 --> F1
    F4 --> S13
    S1 --> M1
```

---

## Process Improvements Summary

| Dimension | Current State | Future State | Improvement |
|---|---|---|---|
| End-to-end processing time | 42 business days | 10 business days | **↓ 76%** |
| Manual touchpoints | 18 | 4 | **↓ 78%** |
| Application error rate | 24% | <3% | **↓ 88%** |
| Staff effort per application | 3.5 hours | 0.5 hours | **↓ 86%** |
| Weekly status calls | 40+ | <5 | **↓ 88%** |
| Audit trail availability | None | 100% | **New capability** |
| Applicant self-service | None | Full portal | **New capability** |
| SIS integration | Manual (separate login) | Automated API | **Eliminated manual step** |
| Finance integration | Manual data entry | Automated API trigger | **Eliminated double-entry** |

---

## Design Principles Applied

1. **Automate the routine, empower the exception** — Staff focus only on cases requiring human judgement
2. **Single source of truth** — All application data in one system; no spreadsheets or email chains
3. **Applicant-centric design** — Full self-service visibility eliminates information asymmetry
4. **Integration over re-entry** — Every system-to-system touchpoint automated via API
5. **Audit by design** — Every action timestamped and attributed to a named user from day one

---

*Related: See [business-requirements-doc.md](../requirements/business-requirements-doc.md) for full requirements tracing.*

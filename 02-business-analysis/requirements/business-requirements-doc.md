# Business Requirements Document (BRD)

> **Document Control**

| Field | Detail |
|---|---|
| **Project Name** | [Project Name] |
| **Project ID** | [PRJ-YYYY-XXX] |
| **Document Version** | 1.0 |
| **Status** | Draft / Under Review / Approved |
| **Business Analyst** | Albert Ibe, CBAP |
| **Business Owner** | [Name, Title] |
| **Date Created** | [YYYY-MM-DD] |
| **Date Approved** | [YYYY-MM-DD] |
| **Next Review Date** | [YYYY-MM-DD] |

---

## 1. Executive Summary

### 1.1 Business Problem
*State the problem clearly in business language. Avoid technical jargon.*

[Example: The Student Services department currently manages scholarship applications through a manual paper-based process requiring 6 weeks of processing time and 3 FTE staff. Applicants have no visibility into their application status, resulting in 40+ weekly status enquiry calls to the department. An automated scholarship management system is required to reduce processing time, improve applicant experience, and free staff capacity for higher-value work.]

### 1.2 Proposed Solution Overview
*High-level description of the proposed solution — what it will do, not how it will be built.*

[Brief solution description]

### 1.3 Expected Business Benefits

| Benefit | Measurement | Target |
|---|---|---|
| [Processing time reduction] | [Days to process application] | [From X to Y days] |
| [Cost saving] | [Annual labour cost] | [$X reduction] |
| [Quality improvement] | [Error rate] | [From X% to Y%] |
| [Stakeholder satisfaction] | [NPS / survey score] | [Target score] |

---

## 2. Business Context

### 2.1 Current State (As-Is)
*Describe how the business operates today. Reference the As-Is process map.*

[Current state description]

→ See [current-state-process.md](../process-maps/current-state-process.md)

### 2.2 Key Pain Points

| # | Pain Point | Affected Stakeholder | Business Impact |
|---|---|---|---|
| 1 | [Pain point description] | [Who is affected] | [Quantified impact if possible] |
| 2 | [Pain point description] | [Who is affected] | [Quantified impact if possible] |
| 3 | [Pain point description] | [Who is affected] | [Quantified impact if possible] |

### 2.3 Future State (To-Be)
*Describe how the business will operate after the solution is implemented.*

[Future state description]

→ See [future-state-process.md](../process-maps/future-state-process.md)

---

## 3. Scope

### 3.1 In Scope
- [Business process / function / department included]
- [System or data in scope]
- [User group in scope]

### 3.2 Out of Scope
- [Explicitly excluded items]
- [Future phase items]

---

## 4. Stakeholders

| Stakeholder | Role | Involvement in Requirements |
|---|---|---|
| [Name] | [Business Owner] | [Approved requirements] |
| [Name] | [SME] | [Provided input] |
| [Name] | [End User Representative] | [Reviewed and validated] |

→ Full stakeholder analysis: [stakeholder-register.csv](../../registers/stakeholder-register.csv)

---

## 5. Business Requirements

> **Requirement ID Format:** BR-[Category]-[Number]  
> **Categories:** FUNC (Functional) | DATA | INT (Integration) | SEC (Security) | PERF (Performance) | COMP (Compliance)

### 5.1 Functional Requirements

| Req ID | Requirement | Priority | Source | Acceptance Criteria | Status |
|---|---|---|---|---|---|
| BR-FUNC-001 | The system shall allow applicants to submit scholarship applications online without requiring in-person attendance | Must Have | Business Owner | Applicant can complete and submit full application via web browser without staff assistance | Draft |
| BR-FUNC-002 | The system shall send automated email confirmation to applicants within 5 minutes of successful submission | Must Have | Business Owner | 100% of submissions trigger confirmation email within 5 minutes | Draft |
| BR-FUNC-003 | The system shall allow applicants to track their application status in real time via a self-service portal | Must Have | End Users | Status updates visible within 2 hours of any status change | Draft |
| BR-FUNC-004 | The system shall generate a ranked scoring report for the review committee based on predefined eligibility criteria | Must Have | Business Owner | Scoring report generated automatically with no manual calculation required | Draft |
| BR-FUNC-005 | The system shall allow review committee members to record decisions and comments directly in the system | Should Have | Committee Members | Decision recorded with timestamp and reviewer identity | Draft |
| BR-FUNC-006 | The system shall send automated award notification and rejection emails to applicants upon committee decision | Must Have | Business Owner | 100% of applicants notified within 24 hours of final committee decision | Draft |
| BR-FUNC-007 | The system shall generate a summary report of all applications by program, status, and award value for management reporting | Should Have | Director | Report exportable to Excel and PDF; available on demand | Draft |
| BR-FUNC-008 | The system shall support bulk import of historical application data from the legacy spreadsheet system | Could Have | IT | Bulk import validated with reconciliation report showing record counts | Draft |

### 5.2 Data Requirements

| Req ID | Requirement | Priority | Source | Acceptance Criteria | Status |
|---|---|---|---|---|---|
| BR-DATA-001 | Applicant personal data (name, SIN, DOB) must be stored in encrypted format at rest | Must Have | Privacy Officer | Data at rest encrypted to AES-256 standard; confirmed by security review | Draft |
| BR-DATA-002 | All application data must be retained for a minimum of 7 years per institutional records retention policy | Must Have | Records Manager | Retention rules configured and verified by Records Manager | Draft |
| BR-DATA-003 | The system must maintain a complete audit trail of all status changes with timestamp and user identity | Must Have | Compliance | Audit log captures 100% of state transitions; exportable for audit review | Draft |
| BR-DATA-004 | Application data must be backed up daily with recovery point objective (RPO) of 24 hours | Must Have | IT Director | Backup schedule confirmed; recovery test completed before go-live | Draft |

### 5.3 Integration Requirements

| Req ID | Requirement | Priority | Source | Acceptance Criteria | Status |
|---|---|---|---|---|---|
| BR-INT-001 | The system must integrate with the Student Information System (SIS) to validate applicant enrollment status | Must Have | Business Owner | Enrollment status validated in real-time at point of application submission | Draft |
| BR-INT-002 | The system must integrate with the Finance system to trigger scholarship payment upon award confirmation | Must Have | Finance Controller | Payment automatically created in Finance system within 1 business day of award confirmation | Draft |
| BR-INT-003 | Single Sign-On (SSO) must be supported using existing Entra ID / Azure AD credentials | Must Have | IT Director | Applicants and reviewers authenticate via institutional SSO with no separate credentials | Draft |

### 5.4 Security Requirements

| Req ID | Requirement | Priority | Source | Acceptance Criteria | Status |
|---|---|---|---|---|---|
| BR-SEC-001 | Role-based access control must ensure applicants can only view their own application data | Must Have | Privacy Officer | Penetration test confirms no cross-applicant data access possible | Draft |
| BR-SEC-002 | Committee reviewer access must be time-limited to the active review period only | Must Have | Business Owner | Access automatically expires at end of review period | Draft |
| BR-SEC-003 | All system access must be logged and available for audit review | Must Have | CISO | 100% of access events logged with user identity and timestamp | Draft |

### 5.5 Performance Requirements

| Req ID | Requirement | Priority | Source | Acceptance Criteria | Status |
|---|---|---|---|---|---|
| BR-PERF-001 | System must support 500 concurrent users during peak application periods | Must Have | IT Director | Load test confirms 500 concurrent users with <3 second page load time | Draft |
| BR-PERF-002 | System availability must be 99.5% during business hours (7am–9pm MT) | Must Have | IT Director | Uptime monitoring confirms 99.5% availability measured monthly | Draft |

### 5.6 Compliance Requirements

| Req ID | Requirement | Priority | Source | Acceptance Criteria | Status |
|---|---|---|---|---|---|
| BR-COMP-001 | System must comply with FIPPA (Freedom of Information and Protection of Privacy Act — Alberta) | Must Have | Privacy Officer | Privacy Impact Assessment completed and approved before go-live | Draft |
| BR-COMP-002 | System must comply with WCAG 2.1 AA accessibility standards | Must Have | Accessibility Officer | Accessibility audit completed; no Level A or AA failures | Draft |

---

## 6. Assumptions and Constraints

### Assumptions
1. [Assumption 1]
2. [Assumption 2]

### Constraints
1. [Constraint 1 — budget, timeline, technology]
2. [Constraint 2]

---

## 7. Requirements Sign-Off

| Stakeholder | Role | Approved | Date | Comments |
|---|---|---|---|---|
| [Name] | Business Owner | ☐ Yes ☐ No | | |
| [Name] | IT Director | ☐ Yes ☐ No | | |
| [Name] | Privacy Officer | ☐ Yes ☐ No | | |
| [Name] | Project Manager | ☐ Yes ☐ No | | |

---

## 8. Document Revision History

| Version | Date | Author | Changes |
|---|---|---|---|
| 0.1 | [Date] | Albert Ibe, CBAP | Initial draft for review |
| 1.0 | [Date] | Albert Ibe, CBAP | Approved version following stakeholder review |

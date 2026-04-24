# User Acceptance Testing (UAT) Plan

| Field | Detail |
|---|---|
| **Project Name** | [Project Name] |
| **UAT Lead** | Albert Ibe, CBAP |
| **UAT Start Date** | [YYYY-MM-DD] |
| **UAT End Date** | [YYYY-MM-DD] |
| **Go/No-Go Decision Date** | [YYYY-MM-DD] |
| **Document Version** | 1.0 |

---

## 1. UAT Objectives

1. Confirm the solution meets all approved business requirements documented in the BRD
2. Validate end-to-end business processes function correctly from the user's perspective
3. Identify and resolve defects before production go-live
4. Obtain formal business sign-off confirming readiness to go-live

---

## 2. UAT Scope

### In Scope
- All functional requirements marked as **Must Have** in the BRD
- End-to-end business process scenarios (happy path + key exception paths)
- Integration touchpoints (SIS, Finance, Entra ID SSO)
- Security and access control validation
- Performance under expected load

### Out of Scope
- Technical / unit testing (completed by development team prior to UAT)
- Performance stress testing (handled separately by IT)
- Should Have and Could Have requirements (tested in regression if time permits)

---

## 3. UAT Team

| Role | Name | Department | Responsibility |
|---|---|---|---|
| UAT Lead / Coordinator | Albert Ibe, CBAP | IT / PMO | Plan, coordinate, track, and report UAT |
| Business Owner | [Name] | [Dept] | Final go/no-go decision authority |
| UAT Tester — Applicant Workflow | [Name] | [Dept] | Test all applicant-facing scenarios |
| UAT Tester — Staff Workflow | [Name] | Student Services | Test staff review and admin scenarios |
| UAT Tester — Committee Workflow | [Name] | [Dept] | Test committee review and decision scenarios |
| UAT Tester — Finance Workflow | [Name] | Finance | Test payment trigger and ERP integration |
| Technical Support | [Name] | IT | Resolve technical defects during UAT |
| Vendor Representative | [Name] | [Vendor] | Support defect investigation and fixes |

---

## 4. UAT Test Scenarios

### Module 1 — Applicant Submission

| Test ID | Scenario | Steps | Expected Result | Pass/Fail | Tester | Date | Defect ID |
|---|---|---|---|---|---|---|---|
| UAT-001 | Successful application submission | 1. Login via SSO 2. Complete all form fields 3. Upload documents 4. Submit | Application submitted; confirmation email received within 5 minutes; status visible in portal | | | | |
| UAT-002 | Incomplete application — missing documents | 1. Login 2. Complete form 3. Skip document upload 4. Attempt submit | System blocks submission; highlights missing fields; no confirmation sent | | | | |
| UAT-003 | Incomplete application — missing required fields | 1. Login 2. Leave mandatory fields blank 3. Attempt submit | System highlights all blank mandatory fields; submit blocked | | | | |
| UAT-004 | Applicant status tracking | 1. Submit application 2. Navigate to status portal | Current application status displayed accurately; updates within 2 hours of any change | | | | |
| UAT-005 | SSO authentication | 1. Navigate to application portal 2. Login with institutional credentials | Redirected to Entra ID login; authenticated without separate credentials | | | | |
| UAT-006 | Duplicate application prevention | 1. Submit application 2. Attempt to submit second application for same scholarship | System detects duplicate; blocks second submission; displays appropriate message | | | | |

### Module 2 — Staff Review and Administration

| Test ID | Scenario | Steps | Expected Result | Pass/Fail | Tester | Date | Defect ID |
|---|---|---|---|---|---|---|---|
| UAT-007 | Application queue visibility | 1. Login as Staff 2. Navigate to application dashboard | All submitted applications visible; filterable by status, program, date | | | | |
| UAT-008 | Automatic enrollment verification | 1. Review a submitted application | SIS enrollment status displayed automatically; no manual verification step required | | | | |
| UAT-009 | Eligibility scoring | 1. Open a complete application | Eligibility score calculated and displayed automatically based on criteria | | | | |
| UAT-010 | Route to committee | 1. Confirm shortlist 2. Submit to committee | Committee members notified automatically; applications appear in committee queue | | | | |
| UAT-011 | Exception handling — ineligible applicant | 1. Submit application with enrollment status "Withdrawn" | Application flagged as ineligible automatically; staff notified | | | | |
| UAT-012 | Management reporting | 1. Login as Manager 2. Generate application summary report | Report shows all applications by program, status, and award value; exportable to Excel and PDF | | | | |

### Module 3 — Committee Review

| Test ID | Scenario | Steps | Expected Result | Pass/Fail | Tester | Date | Defect ID |
|---|---|---|---|---|---|---|---|
| UAT-013 | Committee member access | 1. Login as committee member | Only assigned applications visible; access limited to review period | | | | |
| UAT-014 | Record decision | 1. Open application 2. Select decision 3. Add comments 4. Save | Decision and comments saved with timestamp and reviewer identity | | | | |
| UAT-015 | Committee chair final approval | 1. Login as Chair 2. Review all decisions 3. Confirm final award list | Award list confirmed; Finance payment trigger initiated; applicants notified | | | | |
| UAT-016 | Committee access expiry | 1. Attempt login after review period end date | Access denied; appropriate message displayed | | | | |

### Module 4 — Finance Integration

| Test ID | Scenario | Steps | Expected Result | Pass/Fail | Tester | Date | Defect ID |
|---|---|---|---|---|---|---|---|
| UAT-017 | Payment record auto-creation | 1. Chair confirms award list | Payment records created in ERP within 1 business day; no manual data entry required | | | | |
| UAT-018 | Payment confirmation notification | 1. Payment processed in ERP | Applicant receives payment confirmation email automatically | | | | |
| UAT-019 | Award amount accuracy | 1. Review ERP payment record vs. award list | Payment amount matches approved award exactly | | | | |

### Module 5 — Security and Access Control

| Test ID | Scenario | Steps | Expected Result | Pass/Fail | Tester | Date | Defect ID |
|---|---|---|---|---|---|---|---|
| UAT-020 | Applicant data isolation | 1. Login as Applicant A 2. Attempt to view Applicant B's application | Access denied; only own data visible | | | | |
| UAT-021 | Unauthorized access attempt | 1. Attempt to access admin functions as applicant | Access denied; appropriate error displayed | | | | |
| UAT-022 | Audit log completeness | 1. Perform 5 system actions 2. Review audit log | All 5 actions recorded with timestamp and user identity | | | | |

---

## 5. Defect Management

### Defect Severity Definitions

| Severity | Definition | Resolution SLA |
|---|---|---|
| **Critical (P1)** | System crash, data loss, security breach, or complete blocking of key business process | Fix within 24 hours; retest before UAT continues |
| **High (P2)** | Key business function does not work; no workaround available | Fix within 3 business days |
| **Medium (P3)** | Function works but not as specified; workaround available | Fix within 5 business days |
| **Low (P4)** | Minor UI issue, cosmetic defect, or enhancement request | Fix before go-live or defer to Phase 2 |

### Defect Log

| Defect ID | Test ID | Date Found | Severity | Description | Steps to Reproduce | Assigned To | Status | Resolution Date |
|---|---|---|---|---|---|---|---|---|
| DEF-001 | | | | | | | Open | |

---

## 6. UAT Entry and Exit Criteria

### Entry Criteria (UAT cannot start until ALL are met)
- [ ] Development complete and unit testing passed
- [ ] Test environment configured and stable
- [ ] Test data loaded and validated
- [ ] UAT test scripts reviewed and approved by Business Owner
- [ ] UAT team briefed and available
- [ ] All Must Have requirements in scope are available to test

### Exit Criteria (UAT sign-off requires ALL to be met)
- [ ] All Must Have test scenarios executed
- [ ] 0 open Critical (P1) or High (P2) defects
- [ ] ≤3 open Medium (P3) defects with accepted workarounds
- [ ] Business Owner formal sign-off obtained
- [ ] UAT summary report issued

---

## 7. Go / No-Go Recommendation

*Completed by UAT Lead at end of UAT period.*

| Criterion | Status | Notes |
|---|---|---|
| All P1 defects resolved | ☐ Yes ☐ No | |
| All P2 defects resolved | ☐ Yes ☐ No | |
| P3 defects accepted by Business Owner | ☐ Yes ☐ No | |
| Business Owner sign-off obtained | ☐ Yes ☐ No | |
| Training completed | ☐ Yes ☐ No | |
| Rollback plan confirmed | ☐ Yes ☐ No | |

**UAT Lead Recommendation:** ☐ GO ☐ NO-GO

**Business Owner Decision:** ☐ GO ☐ NO-GO

| Signature | Name | Date |
|---|---|---|
| UAT Lead | | |
| Business Owner | | |
| Project Manager | | |

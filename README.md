# CRM System Upgrade: Salesforce Build (Phase 1)

A personal Business Analyst portfolio project. I took a CRM Business Requirements Document (BRD), built the most important requirements in Salesforce, tested them against user stories, and documented everything.

> **Sample data only.** North Texas Solutions is a sample company. All accounts, contacts, deals and cases are made up for practice. This is not client work.

---

## The problem

A small, growing company is moving its sales and service team off spreadsheets and email onto its first CRM. Today:

- Managers can't see the sales pipeline in one place.
- Sales reps can give any discount, with no review.
- Customer issues get lost in inboxes.
- Reports are built by hand every week.
- Everyone can see every deal's value.

## What I built

| Business need | What I built in Salesforce |
|---|---|
| One customer record | Accounts and contacts linked together, plus an **Industry Segment** field |
| Track leads and deals | Lead conversion (lead to account, contact and deal in one click) and a **Kanban pipeline** by stage |
| Control discounts | A **validation rule** that blocks discounts over 40%, and a **Flow** that flags discounts over 20% and creates a High priority "Review discount" task for the deal owner |
| Handle customer issues | **Cases** with priority and status, and an **Open High Priority** list view |
| Live reporting | 3 reports and a **Sales & Service Overview** dashboard |
| Keep deal values private | **Private** sharing for opportunities and a role hierarchy (CEO > Sales Manager > Sales Rep) |

Everything is built with standard Salesforce configuration (no custom code).

## Scope decisions

My BRD had 10 requirements ranked with MoSCoW. Phase 1 delivers 6 of them.

| Requirement | Priority | Phase |
|---|---|---|
| FR-001 Customer data, FR-002 Pipeline, FR-003 Reporting | Must Have | **Phase 1** |
| FR-006 Workflow automation, FR-007 Cases, FR-008 Custom fields | Should Have | **Phase 1** |
| FR-004 Marketing integration, FR-005 Offline mobile | Must Have | Phase 2 (needs outside systems) |
| FR-009 Documents, FR-010 ERP integration | Could Have | Phase 2 |

## How I tested it

I wrote **9 user stories** with Given / When / Then acceptance criteria and ran **11 test cases**, including negative tests (for example, a 15% discount must *not* trigger a review).

**3 defects found and fixed:**

1. **Flow wouldn't activate.** The task's "Assigned To" pointed at the whole record instead of the owner field. Fixed the mapping.
2. **Open cases report showed 4, not 3.** The report filter was right; the test case had never been closed. Enabled closed statuses and closed the case.
3. **Pipeline KPI showed $205,000.** It included won and lost deals. Built an "Open Pipeline" report (deals not closed): **$163,000**.

## Results

| Measure | Result |
|---|---|
| Custom fields | 3 |
| Sample records | 26 (6 accounts, 6 contacts, 3 leads, 7 deals, 4 cases) |
| Automation | 1 validation rule, 1 record-triggered Flow |
| Reporting | 3 reports, 1 list view, 1 dashboard |
| Tests | 11 passed |
| Defects | 3 found, 3 fixed |
| Open pipeline | $163,000 across 5 deals |

## Files in this folder

| File | What it is |
|---|---|
| `01_CRM_BRD.docx` | Business Requirements Document: the problem, goals, scope, stakeholders, requirements |
| `02_CRM_FRD.docx` | Functional Requirements Document: exact fields, rules, Flow, reports and security settings |
| `03_CRM_User_Stories_and_Acceptance_Criteria.docx` | User stories, test cases and defect log |
| `04_CRM_Business_Process_Model.docx` | As-is vs to-be, and two BPMN swimlane diagrams |
| `05_CRM_Salesforce_App_Build.docx` | What was built, part by part, with screenshots |
| `Diagrams/` | BPMN process diagrams (PNG) |
| `Screenshots/` | Evidence from the Salesforce org |

## What's next (Phase 2)

- Marketing integration and offline mobile access
- A due date on the review task, and a formal approve/reject process
- Log in as a test Sales Rep to prove privacy end to end
- Flag older deals that were already over 20% before go-live

## Tools

Salesforce (Lightning Experience, Developer Edition): Object Manager, Validation Rules, Flow Builder, Reports & Dashboards, Roles, Sharing Settings · Microsoft Word · BPMN

---
*Bhavna Rao, Business Analyst*

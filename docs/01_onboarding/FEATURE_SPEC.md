# Company Onboarding

> **Entity**: Company, User  
> **Status**: 🔴 TODO  
> **Version**: V1.0

---

## Problem

New customer needs:
- OneDrive connected
- Folder structure configured
- Users created with roles
- Cost categories defined

Without smooth onboarding, the product fails at first impression.

---

## Solution

Guided wizard: 8 steps, < 10 minutes.

---

## Entity Reference

See [DATA_MODEL.md → Company](../00_overview/DATA_MODEL.md#company)
See [DATA_MODEL.md → User](../00_overview/DATA_MODEL.md#user)

---

## Invariants

1. Company must have at least one admin user
2. OneDrive must be connected before creating jobs
3. Email unique across all users
4. At least 5 standard cost categories

---

## Onboarding Flow

```
Sign Up → Company Profile → Connect OneDrive → Choose Template → Customize Categories → Create Users → Connect Email → Create First Job
```

| Step | Required | Notes |
|------|----------|-------|
| Sign Up | Yes | Email, password |
| Company Profile | Yes | Name required, rest optional |
| Connect OneDrive | Yes | OAuth with Microsoft |
| Choose Template | Yes | Pre-built options |
| Customize Categories | Optional | Defaults provided |
| Create Users | Optional | Can add later |
| Connect Email | Optional | Outlook OAuth |
| Create First Job | Optional | Guided walkthrough |

---

## Folder Templates

| Template | Industries | Extra Folders |
|----------|------------|---------------|
| Waterproofing | Waterproofing, roofing | Substrate Prep, Membrane |
| Steel Fabrication | Steel, structural | Fab Drawings, Install |
| General Subcontractor | Electrical, plumbing | Standard only |
| Builder | Head contractors | Trades, Subcon Management |

### Standard Folders (All Templates)

```
01_Contracts
02_Quotes_and_Variations
03_Invoices_and_Claims
04_Bills_and_POs
05_Site_and_Delivery
06_Job_Information
07_QA_and_Compliance
```

---

## Cost Categories (Default)

| Category | Default Markup |
|----------|----------------|
| Labour | 30% |
| Materials | 15% |
| Plant & Equipment | 20% |
| Subcontractors | 10% |
| Other | 15% |

---

## User Roles

| Role | Permissions |
|------|-------------|
| Admin | Full access, manage users, settings |
| PM | Jobs, variations, day sheets, reports |
| Estimator | Quotes, variations |
| Supervisor | Day sheets, timesheets, QA |
| Accounts | Invoicing, billing, suppliers |
| Viewer | Read-only |

---

## Integration Points

### Microsoft Graph (OneDrive)

| Scope | Purpose |
|-------|---------|
| Files.ReadWrite.All | Create/read/write files |
| offline_access | Maintain connection |

### Microsoft Graph (Outlook)

| Scope | Purpose |
|-------|---------|
| Mail.Read | Read emails |
| Mail.ReadWrite | Send emails |
| offline_access | Maintain connection |

---

## Open Questions

| Question | Status |
|----------|--------|
| OneDrive disconnects? | Need graceful degradation |
| Multi-company users? | No for V1 |
| Storage limits? | Customer's responsibility |

---

## Acceptance Criteria

- [ ] Admin can sign up and create company
- [ ] Admin can connect OneDrive via OAuth
- [ ] Admin can select folder template
- [ ] Admin can customize cost categories
- [ ] Admin can create users with roles
- [ ] Admin can optionally connect Outlook
- [ ] Onboarding completes in < 10 minutes

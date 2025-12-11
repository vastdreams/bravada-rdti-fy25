# Quotech — Product Vision

> **Version**: 0.2 (First Principles)  
> **Last Updated**: December 2024

---

## The Problem

### What's Broken

Subcontractors operate with information **scattered across**:

| Source | Reality |
|--------|---------|
| Individual inboxes | Critical instructions buried in 50+ daily emails |
| Ad-hoc folders | OneDrive/SharePoint with inconsistent naming |
| Desktop downloads | Files on personal machines, not shared |
| Multiple systems | Simpro, Xero, Excel, WhatsApp |
| Paper | Day sheets, sign-offs, QA forms |

### The Consequences

1. **Nobody has the full picture** of any job
2. **Variations and instructions get missed** → revenue leaks
3. **QA and disputes are painful** → evidence is buried
4. **New team members take weeks** to load context
5. **Profit leaks undetected** → no real-time cost visibility
6. **Manual data entry** → hours wasted daily

### Root Cause

> There is no **single, structured, searchable workspace** per job that captures files, emails, quotes, variations, and site data together.

---

## The Solution

### Core Concept

Quotech creates a **structured overlay** on the customer's OneDrive, transforming scattered artifacts into an organised, searchable, AI-enhanced workspace.

```
┌─────────────────────────────────────────┐
│           QUOTECH JOBS HUB              │
│  ┌───────────────────────────────────┐  │
│  │  AI Classification + Search + BI  │  │
│  └───────────────────────────────────┘  │
│                    ▲                     │
│  ┌─────┬─────┬─────┴─────┬─────┬─────┐  │
│  │Files│Email│  Quotes   │ Var │ BI  │  │
│  └──┬──┴──┬──┴─────┬─────┴──┬──┴──┬──┘  │
│     └─────┴────────┴────────┴─────┘     │
│                    ▼                     │
│  ┌───────────────────────────────────┐  │
│  │    OneDrive (Customer's Data)     │  │
│  └───────────────────────────────────┘  │
└─────────────────────────────────────────┘
```

### Key Differentiator

| Principle | What it means |
|-----------|---------------|
| **OneDrive as source of truth** | Customer data stays in their infrastructure; Quotech is an overlay |
| **AI-first organisation** | Folder purpose metadata enables intelligent classification |
| **One place per job** | Everything for a job lives together |
| **Traceable everything** | Every record links to its original source |
| **Emails are documents** | Captured, saved, searchable with files |

---

## Core Entities

The system models **construction project execution** through these entities:

### Primary Entities

| Entity | Purpose | Key Invariants |
|--------|---------|----------------|
| **Company** | Organisation using Quotech | Has OneDrive root, at least one admin user |
| **User** | Person in the system | Has exactly one role, belongs to one company |
| **Job** | Construction project | Has status lifecycle, belongs to one company |
| **Quote** | Pricing proposal | Belongs to one job, has cost items, has version history |
| **Variation** | Scope change | One of three types: scope_change, do_and_charge, mini_project |
| **DaySheet** | T&M work record | Allocated to at most one variation, requires client sign-off |

### Supporting Entities

| Entity | Purpose | Key Invariants |
|--------|---------|----------------|
| **File** | Job document | Stored in OneDrive, has category, indexed for search |
| **Email** | Captured email | Has Outlook ID, has category, saved to OneDrive |
| **CostItem** | Quote line item | Belongs to quote, has cost category |
| **Supplier** | Vendor/Subcontractor | Belongs to company, has many POs |
| **Invoice** | Billing record | Belongs to job, may link to variation |
| **Timesheet** | Worker time entry | Belongs to user and job, has approval workflow |
| **Ticket** | Worker license | Belongs to user, has expiry date |
| **QARecord** | Quality record | Belongs to job, has pass/fail status |

---

## Entity Lifecycle Invariants

### Job Status Lifecycle

```
tender → quoted → won → active → complete → archived
```

| Status | Meaning | Allowed Actions |
|--------|---------|-----------------|
| `tender` | Opportunity received | Create quotes |
| `quoted` | Quote sent, awaiting | Track, revise |
| `won` | Contract signed | Begin execution |
| `active` | Work in progress | Full operations |
| `complete` | Work finished | Final billing |
| `archived` | Fully closed | Read-only |

### Quote Status Lifecycle

```
draft → sent → accepted|rejected|expired
```

### Variation Lifecycle

```
draft → submitted → under_review → approved|rejected → invoiced
```

### DaySheet Lifecycle

```
draft → submitted → approved|rejected
                ↓
           allocated (to variation)
```

---

## Cost Categories (Canonical)

Every cost-related entity uses these categories:

| Category | Code | Examples |
|----------|------|----------|
| **Labour** | `labour` | Direct labour hours, wages |
| **Materials** | `materials` | Products, consumables |
| **Plant & Equipment** | `plant` | Hire, depreciation |
| **Subcontractors** | `subcontractor` | External trade work |
| **Other** | `other` | Permits, testing, misc |

### Category Rules

1. Every `CostItem` has exactly one category
2. Every `SupplierBill` is classified to one category
3. Budget vs Actual reports group by these categories
4. AI classification maps incoming documents to categories

---

## File/Email Classification

### Standard Folder Categories

| Code | Display Name | Purpose |
|------|--------------|---------|
| `01_contracts` | Contracts | Primary contract documents |
| `02_quotes` | Quotes & Variations | Pricing documents |
| `03_invoices` | Invoices & Claims | Billing documents |
| `04_bills` | Bills & POs | Supplier documents |
| `05_site` | Site & Delivery | Site communications |
| `06_info` | Job Information | Reference materials |
| `07_qa` | QA & Compliance | Quality records |

### Classification Priority

1. **User manual assignment** → highest authority
2. **Rule-based patterns** → filename, sender, subject
3. **AI classification** → content analysis
4. **Default to "Other"** → catch-all

---

## Variation Types

Three distinct types with different workflows:

| Type | When Used | Evidence Required |
|------|-----------|-------------------|
| **Scope Change** | Fixed-price change to existing scope | Instruction + revised pricing |
| **Do-and-Charge** | Time & materials work | Signed day sheets |
| **Mini-Project** | New scope as sub-project | Full quote process |

### Variation Invariants

1. Every variation has exactly one type
2. Do-and-charge variations require allocated day sheets
3. Day sheets can only be allocated to ONE variation
4. Approved value flows to job contract value

---

## Target Users

| Persona | Primary Modules | Key Need |
|---------|-----------------|----------|
| **Estimator** | Quotes, Variations | Fast quote creation, cost centre templates |
| **Project Manager** | Jobs, Variations, Day Sheets | Job oversight, variation tracking |
| **Site Supervisor** | Day Sheets, Timesheets, QA | Mobile capture, client sign-offs |
| **Accounts** | Billing, Suppliers | Invoicing, claims, reconciliation |
| **Admin/Director** | Onboarding, Reports | Setup, dashboards, forecasting |

---

## Success Metrics

| Metric | Target | Why |
|--------|--------|-----|
| Time to find document | < 30 seconds | Information accessibility |
| Day sheet capture time | < 2 minutes | Field efficiency |
| Missed variations | Near zero | Revenue protection |
| Invoice turnaround | < 48 hours | Cash flow |
| User adoption | > 80% DAU | Platform stickiness |

---

## Competitive Position

> "Simpro power with Notion simplicity, powered by AI"

| Competitor | Strength | Quotech Advantage |
|------------|----------|-------------------|
| Simpro | Feature-rich | Easier to use, AI-enhanced |
| Tradify | Simple, mobile | More powerful for large projects |
| Procore | Enterprise | More affordable, right-sized |
| Excel/Paper | Familiar | Automated, searchable, connected |

---

*This vision document defines what Quotech is, what entities it manages, and what invariants must hold. All feature decisions should align with these principles.*

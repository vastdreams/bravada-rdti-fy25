# Quotech Project — Comprehensive Technical Context

> **PATH**: 02-evidence/technical/quotech-comprehensive-project-context.md  
> **PURPOSE**: Complete technical documentation of the Quotech R&D project for RDTI filing  
> **LAST UPDATED**: December 2024  
> **SOURCE**: Analysis of 24 specification documents from `/docs` folder

---

## Executive Summary

Quotech is an AI-driven construction project management platform designed to solve the fundamental problem of **information fragmentation in subcontractor operations**. The platform creates a "structured overlay" on the customer's existing Microsoft OneDrive infrastructure, transforming scattered artifacts (files, emails, quotes, variations, site data) into an organised, searchable, AI-enhanced workspace.

### Core Innovation Thesis

> "There is no single, structured, searchable workspace per job that captures files, emails, quotes, variations, and site data together."

Quotech addresses this by treating **every construction job as a unified information hub**, with AI-driven classification, extraction, and insight generation.

---

## 1. Problem Statement

### 1.1 Current Industry Pain Points

| Source | Reality |
|--------|---------|
| Individual inboxes | Critical instructions buried in 50+ daily emails |
| Ad-hoc folders | OneDrive/SharePoint with inconsistent naming |
| Desktop downloads | Files on personal machines, not shared |
| Multiple systems | Simpro, Xero, Excel, WhatsApp |
| Paper | Day sheets, sign-offs, QA forms |

### 1.2 Business Consequences

1. **Nobody has the full picture** of any job
2. **Variations and instructions get missed** → revenue leaks
3. **QA and disputes are painful** → evidence is buried
4. **New team members take weeks** to load context
5. **Profit leaks undetected** → no real-time cost visibility
6. **Manual data entry** → hours wasted daily

### 1.3 Target Users

| Persona | Primary Modules | Key Need |
|---------|-----------------|----------|
| **Estimator** | Quotes, Variations | Fast quote creation, cost centre templates |
| **Project Manager** | Jobs, Variations, Day Sheets | Job oversight, variation tracking |
| **Site Supervisor** | Day Sheets, Timesheets, QA | Mobile capture, client sign-offs |
| **Accounts** | Billing, Suppliers | Invoicing, claims, reconciliation |
| **Admin/Director** | Onboarding, Users, Settings | Setup, dashboards, forecasting |

---

## 2. Solution Architecture

### 2.1 Core Concept

Quotech creates a **structured overlay** on the customer's OneDrive:

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

### 2.2 Key Differentiators (First Principles)

| Principle | Implementation |
|-----------|----------------|
| **One source of truth per job** | All artifacts consolidated in job workspace |
| **Emails = Documents** | Captured, classified, searchable alongside files |
| **AI classifies, humans verify** | Folder purpose metadata guides intelligent routing |
| **Customer owns their data** | OneDrive overlay, not a data silo |
| **Every record is traceable** | Links back to original source |

### 2.3 Competitive Position

> "Simpro power with Notion simplicity, powered by AI"

| Competitor | Strength | Quotech Advantage |
|------------|----------|-------------------|
| Simpro | Feature-rich | Easier to use, AI-enhanced |
| Tradify | Simple, mobile | More powerful for large projects |
| Procore | Enterprise | More affordable, right-sized |
| Excel/Paper | Familiar | Automated, searchable, connected |

---

## 3. Entity Data Model

### 3.1 Entity Hierarchy

```
Company ─────────────────────────────────────────────────────────┐
│                                                                 │
├── Users[] ──────────────────────────────────────────────────┐  │
│   └── Tickets[] (worker licenses)                            │  │
│                                                               │  │
├── Suppliers[] ──────────────────────────────────────────────┐│  │
│                                                              ││  │
└── Jobs[] ────────────────────────────────────────────────────┤│  │
    │                                                          ││  │
    ├── Files[]                                                ││  │
    ├── Emails[]                                               ││  │
    ├── Quotes[] ──────────────────────────────────────────┐   ││  │
    │   └── CostItems[]                                     │   ││  │
    ├── Variations[] ──────────────────────────────────────┼───┤│  │
    │   └── DaySheets[] (allocated)                         │   ││  │
    ├── Invoices[]                                          │   ││  │
    ├── PurchaseOrders[] ───────────────────────────────────┼───┘│  │
    ├── Timesheets[]                                        │    │  │
    └── QARecords[]                                         │    │  │
                                                            └────┴──┘
```

### 3.2 Primary Entities

| Entity | Purpose | Key Invariants |
|--------|---------|----------------|
| **Company** | Organisation using Quotech | Has OneDrive root, at least one admin user |
| **User** | Person in the system | Has exactly one role, belongs to one company |
| **Job** | Construction project | Has status lifecycle, belongs to one company |
| **Quote** | Pricing proposal | Belongs to one job, has cost items, has version history |
| **Variation** | Scope change | One of three types: scope_change, do_and_charge, mini_project |
| **DaySheet** | T&M work record | Allocated to at most one variation, requires client sign-off |

### 3.3 Supporting Entities

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

### 3.4 Entity Lifecycle Invariants

#### Job Status Lifecycle

```
tender → quoted → won → active → complete → archived
```

#### Quote Status Lifecycle

```
draft → sent → accepted|rejected|expired
```

#### Variation Lifecycle

```
draft → submitted → under_review → approved|rejected → invoiced
```

#### DaySheet Lifecycle

```
draft → submitted → approved|rejected
                ↓
           allocated (to variation)
```

---

## 4. Module Specifications (14 Modules)

### 4.1 Module Overview

| # | Module | Status | Core Entity |
|---|--------|--------|-------------|
| 01 | Onboarding | 🔴 TODO | Company, User |
| 02 | Jobs Hub | 🔴 TODO | Job |
| 03 | Files & Email | 🔴 TODO | File, Email |
| 04 | Quotes & Tenders | 🔴 TODO | Quote, CostItem |
| 05 | Variations | 🔴 TODO | Variation |
| 06 | Day Sheets | 🔴 TODO | DaySheet |
| 07 | Timesheets | 🔴 TODO | Timesheet |
| 08 | Suppliers & POs | 🔴 TODO | Supplier, PurchaseOrder |
| 09 | Billing & Invoicing | 🔴 TODO | Invoice |
| 10 | BI & Reporting | 🔴 TODO | (Query-based) |
| 11 | QA & Compliance | 🔴 TODO | QARecord |
| 12 | Tickets & Licenses | 🔴 TODO | Ticket |
| 13 | AI & Automation | 🔴 TODO | (Cross-cutting) |
| 14 | Integrations | 🔴 TODO | (External) |

### 4.2 Module Details

#### Module 01: Company Onboarding

**Problem**: New customer needs OneDrive connected, folder structure configured, users created with roles, cost categories defined.

**Solution**: Guided wizard: 8 steps, < 10 minutes.

**Flow**: Sign Up → Company Profile → Connect OneDrive → Choose Template → Customize Categories → Create Users → Connect Email → Create First Job

**Invariants**:
1. Company must have at least one admin user
2. OneDrive must be connected before creating jobs
3. Email unique across all users
4. At least 5 standard cost categories

---

#### Module 02: Jobs Hub

**Problem**: PMs need to see job health at a glance without clicking through multiple screens.

**Solution**: Card-based dashboard with configurable layout. Sidebar provides quick access to files, emails, notes.

**Key Dashboard Cards**:
- Job Summary (Client, Site, Status, Dates)
- P&L (Revenue, Costs, Margin %)
- Labour (Hours budgeted vs actual)
- Variations (Count, Value, Pending)
- Invoices (Invoiced, Paid, Outstanding)
- Day Sheets (Pending approval count)
- AI Insights (Smart alerts)

**Invariants**:
1. Job always has exactly one status
2. Contract value = original quote + sum(approved variations)
3. Completion % = actual cost / budgeted cost
4. User card layout persists per user per job

---

#### Module 03: Files & Email Consolidation

**Problem**: Files scattered across individual inboxes, ad-hoc folders, personal machines, and multiple systems.

**Solution**: Unified workspace where files and emails live together, are searchable in context, and are AI-classified into standard categories.

**Standard Categories**:
- `01_contracts` — Contracts
- `02_quotes` — Quotes & Variations
- `03_invoices` — Invoices & Claims
- `04_bills` — Bills & POs
- `05_site` — Site & Delivery
- `06_info` — Job Information
- `07_qa` — QA & Compliance
- `other` — Uncategorized

**Classification Priority**:
1. User manual assignment (highest authority)
2. Rule-based patterns (filename, sender, subject)
3. AI classification (content analysis)
4. Default to "Other"

**Invariants**:
1. Every File has exactly one category
2. Every Email has exactly one category
3. Files stored in customer's OneDrive (not Quotech servers)
4. Email attachments extracted as separate File entities
5. Original Outlook ID preserved (no duplicate capture)

---

#### Module 04: Quotes & Tender Tracking

**Problem**: Quotes are created in Excel, tracked in spreadsheets, and context is lost when job starts.

**Solution**: Structured quote lifecycle from tender receipt through job conversion, with cost centre templates and AI-assisted import.

**Cost Categories**:
- `labour` — Installation hours, supervision
- `materials` — Membrane, primer, tools
- `plant` — Equipment hire, scaffolding
- `subcontractor` — External trades
- `other` — Permits, testing, contingency

**Invariants**:
1. Quote belongs to exactly one Job
2. Quote number unique per job
3. Revisions link to parent, increment version
4. total_cost = sum(CostItems.total_cost)
5. total_sell = sum(CostItems.total_sell)
6. margin_percent = (sell - cost) / sell × 100
7. When accepted, quote data becomes job budget baseline

---

#### Module 05: Variation Management

**Problem**: Variations are 20-40% of subcontractor revenue. Without systematic tracking: revenue leaks, disputes, cash flow delays, margin erosion.

**Solution**: Three distinct variation types with appropriate workflows:

| Type | When | Evidence | Workflow |
|------|------|----------|----------|
| **Scope Change** | Fixed-price change | Instruction + Quote | Quote → Submit → Approve → Invoice |
| **Do-and-Charge** | Time & materials | Signed Day Sheets | Work → Log → Allocate → Submit → Invoice |
| **Mini-Project** | New scope | Full Quote | Full quote process as sub-project |

**Invariants**:
1. Every variation has exactly one type
2. `do_and_charge` variations require at least one allocated day sheet
3. Day sheets can be allocated to at most ONE variation
4. `approved_value` flows to Job.contract_value when status = approved
5. Variation number is unique per job (V001, V002, ...)

---

#### Module 06: Day Sheet Capture

**Problem**: Day work (T&M) is often forgotten, under-claimed, disputed, delayed.

**Solution**: Two capture methods:
- **Create in App**: Form input, digital signature
- **Scan to Structure**: Photo → OCR → AI extraction (V2)

**Invariants**:
1. Day sheet can be allocated to at most ONE variation
2. Submission requires client signature
3. Total hours = sum(workers[].hours)
4. Labour value = sum(workers[].hours × workers[].hourly_rate)
5. Date cannot be in future
6. At least one worker with hours > 0

---

#### Module 07: Timesheets

**Problem**: Labour is the biggest cost. Late or inaccurate time capture erodes margin and delays billing/payroll.

**Solution**: Simple clock-in/out + submission + PM approval with GPS and break handling.

**Invariants**:
1. `total_hours = (end_time - start_time) - break_minutes/60`
2. `total_hours > 0`; date not in future
3. Belongs to exactly one Job and one User
4. No overlapping entries per user per time range

---

#### Module 08: Suppliers & Purchase Orders

**Problem**: Untracked purchasing causes cost overruns and paying for undelivered goods.

**Solution**: Simple PO flow: create → send → acknowledge → deliver → match bill → close.

**Invariants**:
1. PO belongs to exactly one Job and one Supplier
2. PO number unique per company
3. PO total = sum(item.total)
4. PO PDF stored in OneDrive

---

#### Module 09: Billing & Invoicing

**Problem**: Slow or inconsistent claims delay cash flow and cause disputes.

**Solution**: Generate claims/invoices with evidence, track through approval to payment.

**Claim Calculation**:
```
Work Value       = Contract Value × % Complete
Variations       = Sum(Approved Variations)
Less Prev Claims = Sum(Previous Claims)
Retention        = Contract Retention %
----------------------------------------------------
Claim Amount
```

**Invariants**:
1. Invoice belongs to exactly one Job
2. Invoice number unique per company
3. Claim amount = f(contract value, % complete, approved variations, previous claims, retention)
4. PDF stored in OneDrive; evidence attached

---

#### Module 10: BI & Reporting

**Problem**: Financial data scattered across Simpro, Xero, Excel. No unified view of profitability.

**Solution**: Query-based reporting from Quotech data. Real-time budget vs actual at job, variation, and category level.

**Core Calculations**:
```
Contract Value = Original Quote + Sum(Approved Variations)
Revenue to Date = Sum(Invoices where status in [sent, approved, paid])
Cost to Date = Labour Cost + Materials Cost + Subcon Cost + Plant Cost + Other Cost
Gross Profit = Revenue - Cost
Margin % = Gross Profit / Revenue × 100
```

---

#### Module 11: QA & Compliance

**Problem**: Unstructured QA leads to defects, rework, and weak evidence at handover.

**Solution**: Checklists/inspections per job & area with pass/fail, photos, signatures.

**Invariants**:
1. QARecord belongs to one Job
2. Status ∈ {pass, fail, pending, na}
3. Submission requires inspector sign-off
4. Photos/form data stored; PDF saved to QA folder

---

#### Module 12: Tickets & Licenses

**Problem**: Expired or missing licenses risk safety, non-compliance, and site access issues.

**Solution**: Track worker tickets/inductions with OCR capture, expiry monitoring.

**Status Logic**:
```
if no expiry_date -> valid
else if today > expiry_date -> expired
else if expiry_date - today ≤ 30 days -> expiring_soon
else -> valid
```

---

#### Module 13: AI & Automation

**Problem**: Manual processes for filing documents, classifying emails, extracting data from scans, identifying trends.

**Solution**: AI-powered classification, extraction, and insight generation. Humans verify and override.

**AI Capabilities by Phase**:

| Phase | Capabilities |
|-------|--------------|
| **V1.0 — Foundation** | Email Classification, File Classification, Smart Search, Basic OCR |
| **V2.0 — Automation** | Day Sheet OCR, Ticket OCR, Project Notebook, Quote Reader |
| **V3.0 — Intelligence** | Contract Analysis, Quote Builder, Predictive Analytics, NL Queries, AI Insights Feed |

**Classification Engine**:

| Signal | Weight | Example |
|--------|--------|---------|
| Subject keywords | High | "Quote", "Variation", "Invoice" |
| Sender domain | Medium | Known client domains |
| Thread context | High | Reply to captured email |
| Body content | Medium | AI analysis |
| Attachment types | Low | PDF, Excel |

---

#### Module 14: Integrations

**Problem**: Data lives in customer systems. Without integration, users duplicate effort.

**Solution**: Minimal, secure connections to customer systems.

**V1 Core Integrations**:
- **OneDrive (Graph)**: Files/folders per job
- **Outlook (Graph)**: Email capture/send

**V2 Extended**:
- **Xero**: Invoices/bills sync
- **Simpro (import)**: Migration

---

## 5. Technical Uncertainty Areas (R&D Focus)

Based on the documentation analysis, the following areas represent significant technical uncertainty requiring systematic investigation:

### 5.1 AI Classification Engine

**Uncertainty**: Can AI reliably classify construction-industry emails and documents into the correct job and category with sufficient accuracy (>85%) to enable auto-assignment?

**Signals**: Subject keywords, sender domain, thread context, body content, attachment types

**Unknown Outcomes**:
- Optimal confidence thresholds for auto-assign vs suggest vs flag
- Learning rate from user corrections
- Cross-company model transferability

### 5.2 OCR + AI Data Extraction

**Uncertainty**: Can we reliably extract structured data from paper day sheets (worker names, hours, materials, signatures) using OCR + LLM parsing?

**Extraction Difficulty**:
- Date: Easy
- Worker names: Medium
- Hours: Medium
- Materials: Hard
- Description: Medium
- Signature present: Easy

**Unknown Outcomes**:
- Error rates across different handwriting styles
- Validation workflows for low-confidence extraction
- Photo quality requirements

### 5.3 Contract Analysis Agent

**Uncertainty**: Can AI reliably extract key terms and identify risks from construction contracts with varying formats and legal complexity?

**Extraction Targets**:
- Contract value and payment terms
- Scope summary
- Key dates (start, completion, DLP)
- Retention terms
- Insurance requirements
- Liquidated damages
- Variation process
- Dispute resolution

### 5.4 Quote Ingestor (DeepSeek)

**Uncertainty**: Can AI parse diverse Excel/PDF quote formats and reliably map to Quotech's CostItem schema?

**Column Mapping Challenges**:
- Variable header naming ("Qty" vs "Quantity" vs "Units")
- Category inference from descriptions
- Handling multi-level section structures

### 5.5 Real-Time Financial Calculations

**Uncertainty**: Can we compute job profitability, budget vs actual, and forecasts in real-time across large datasets while maintaining <2 second response times?

**Calculation Complexity**:
- Contract Value = Original Quote + Sum(Approved Variations)
- Revenue to Date = Sum(Invoices where status in [sent, approved, paid])
- Cost to Date = Sum(Timesheets × rate) + Sum(Supplier Bills)
- Forecast Cost = Actual to Date / Completion % × 100

---

## 6. Technology Stack

### 6.1 Frontend (from GitLab analysis)

- **React 19** — Core UI framework (cutting-edge)
- **Vite 6** — Build tooling
- **Redux Toolkit** — State management
- **Tailwind CSS** — Styling
- **Radix UI** — Accessible components
- **ApexCharts** — Data visualization
- **FullCalendar** — Calendar/scheduling
- **XLSX** — Excel file processing

### 6.2 AI/ML Stack

| Component | Options |
|-----------|---------|
| LLM | DeepSeek (structured), GPT-4 (reasoning), Claude (docs) |
| OCR | Google Vision, AWS Textract |
| Search | Elasticsearch, Pinecone (vector) |
| Classification | Custom model + LLM |

### 6.3 Integrations

| System | Purpose | Scopes |
|--------|---------|--------|
| OneDrive (Graph) | Files/folders per job | `Files.ReadWrite.All`, `offline_access` |
| Outlook (Graph) | Email capture/send | `Mail.ReadWrite`, `Mail.Send`, `offline_access` |
| Xero (V2) | Invoices/bills sync | `accounting.transactions`, `offline_access` |

---

## 7. Product Roadmap

| Phase | Focus | Key Deliverables |
|-------|-------|------------------|
| **V1.0** | Information Consolidation | OneDrive, Email Ingestion, Jobs Hub, Basic BI |
| **V2.0** | Automation Layer | Day Sheet OCR, Timesheet App, Ticket OCR |
| **V3.0** | Intelligence | Quote Builder, Contract Analysis, Forecasting |

---

## 8. Success Metrics

| Metric | Target | Why |
|--------|--------|-----|
| Time to find document | < 30 seconds | Information accessibility |
| Day sheet capture time | < 2 minutes | Field efficiency |
| Missed variations | Near zero | Revenue protection |
| Invoice turnaround | < 48 hours | Cash flow |
| User adoption | > 80% DAU | Platform stickiness |
| Quote turnaround | < 5 days | Sales velocity |
| DSO (Days Sales Outstanding) | < 45 days | Collection efficiency |
| Job margin accuracy | ± 5% | Financial control |

---

## 9. R&D Evidence Summary

This documentation demonstrates:

### 9.1 Technical Uncertainty

- AI classification accuracy for construction documents
- OCR extraction from variable paper formats
- Real-time financial computation at scale
- Multi-modal integration (OneDrive + Outlook + Xero)
- Contract analysis with legal complexity

### 9.2 Systematic Investigation

- 24 feature specification documents with structured approach
- Data model with explicit invariants and constraints
- User flow documentation for 5 distinct personas
- Phased roadmap (V1 → V2 → V3) showing iterative development
- Clear acceptance criteria per module

### 9.3 Technical Advancement

- Novel application of LLMs to construction document classification
- Integration of OCR + AI for structured data extraction from day sheets
- Real-time BI across disparate data sources
- OneDrive overlay architecture (customer data ownership)
- AI-assisted quote ingestion from Excel/PDF

---

## 10. Document References

This context was synthesized from:

| Document | Lines | Coverage |
|----------|-------|----------|
| PRODUCT_VISION.md | ~243 | Problem, Solution, Entities |
| DATA_MODEL.md | ~519 | Entity definitions, relationships |
| CURRENT_STATE_MAPPING.md | ~1912 | Complete UI/UX reference |
| CURRENT_STATE_FLOWS.md | ~576 | Navigation & data flow diagrams |
| INDEX.md | ~131 | Documentation structure |
| 14 Feature Specifications | ~3500 | Module-level requirements |
| 5 User Flow Documents | ~600 | Persona workflows |

---

*This document provides comprehensive technical context for the Quotech R&D project. It serves as evidence of systematic investigation and technical advancement for RDTI compliance.*

---

## Future Notes for AI

1. **When adding new modules**: Follow the existing feature spec template (Current State → Problem → Entities → Invariants → Workflows → UI → Integration Points → Open Questions → Acceptance Criteria)

2. **When modifying data model**: Ensure all invariants are maintained; update affected modules

3. **AI Classification tuning**: Store all corrections for retraining; monitor confidence distribution over time

4. **OCR pipeline**: Preserve original scans; implement fallback to manual entry for low-confidence extraction

5. **Performance optimization**: Consider materialized views for BI queries; refresh on demand or scheduled (every 15 min)

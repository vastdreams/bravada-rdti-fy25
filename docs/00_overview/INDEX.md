# Quotech — Documentation Index

> **Version**: 0.2 (Restructured to First Principles)  
> **Last Updated**: December 2024

---

## What is Quotech?

**The Job Hub.** Every job's files, emails, quotes, variations, and site data in one organised workspace.

---

## First Principles

| Principle | Implementation |
|-----------|----------------|
| **One source of truth per job** | All artifacts consolidated in job workspace |
| **Emails = Documents** | Captured, classified, searchable alongside files |
| **AI classifies, humans verify** | Folder purpose metadata guides intelligent routing |
| **Customer owns their data** | OneDrive overlay, not a data silo |
| **Every record is traceable** | Links back to original source |

---

## Documentation Map

### Layer 0: Foundation

| Document | Purpose |
|----------|---------|
| **[PRODUCT_VISION.md](./PRODUCT_VISION.md)** | Problem → Solution → Entities → Invariants |
| **[DATA_MODEL.md](./DATA_MODEL.md)** | Entity definitions, relationships, constraints |

### Layer 1: Current State (From Screenshot Analysis)

| Document | Lines | Coverage |
|----------|-------|----------|
| **[CURRENT_STATE_MAPPING.md](./CURRENT_STATE_MAPPING.md)** | ~1800 | Complete UI/UX reference |
| **[CURRENT_STATE_FLOWS.md](./CURRENT_STATE_FLOWS.md)** | ~570 | Navigation & data flow diagrams |

### Layer 2: Feature Specifications

| # | Module | Status | Core Entity |
|---|--------|--------|-------------|
| 01 | [Onboarding](../01_onboarding/FEATURE_SPEC.md) | 🔴 | Company, User |
| 02 | [Jobs Hub](../02_jobs_hub/FEATURE_SPEC.md) | 🔴 | Job |
| 03 | [Files & Email](../03_files_and_email/FEATURE_SPEC.md) | 🔴 | File, Email |
| 04 | [Quotes & Tenders](../04_quotes_and_tenders/FEATURE_SPEC.md) | 🔴 | Quote, CostItem |
| 05 | [Variations](../05_variations/FEATURE_SPEC.md) | 🔴 | Variation |
| 06 | [Day Sheets](../06_day_sheets/FEATURE_SPEC.md) | 🔴 | DaySheet |
| 07 | [Timesheets](../07_timesheets/FEATURE_SPEC.md) | 🔴 | Timesheet |
| 08 | [Suppliers & POs](../08_suppliers_and_pos/FEATURE_SPEC.md) | 🔴 | Supplier, PurchaseOrder |
| 09 | [Billing & Invoicing](../09_billing_and_invoicing/FEATURE_SPEC.md) | 🔴 | Invoice |
| 10 | [BI & Reporting](../10_bi_and_reporting/FEATURE_SPEC.md) | 🔴 | (Query-based) |
| 11 | [QA & Compliance](../11_quality_and_compliance/FEATURE_SPEC.md) | 🔴 | QARecord |
| 12 | [Tickets & Licenses](../12_tickets_and_licenses/FEATURE_SPEC.md) | 🔴 | Ticket |
| 13 | [AI & Automation](../13_ai_and_automation/FEATURE_SPEC.md) | 🔴 | (Cross-cutting) |
| 14 | [Integrations](../14_integrations/FEATURE_SPEC.md) | 🔴 | (External) |

### Layer 3: User Flows (By Persona)

| Persona | Primary Modules | Document |
|---------|-----------------|----------|
| Estimator | Quotes, Variations | [estimator.md](../user_flows/estimator.md) |
| Project Manager | Jobs, Variations, Day Sheets | [project_manager.md](../user_flows/project_manager.md) |
| Site Supervisor | Day Sheets, Timesheets, QA | [site_supervisor.md](../user_flows/site_supervisor.md) |
| Accounts | Billing, Suppliers | [accounts.md](../user_flows/accounts.md) |
| Admin | Onboarding, Users, Settings | [admin.md](../user_flows/admin.md) |

---

## Entity Dependency Graph

```
Company
├── Users (many)
├── Suppliers (many)
└── Jobs (many)
    ├── Files (many)
    ├── Emails (many)
    ├── Quotes (many)
    │   └── CostItems (many)
    ├── Variations (many)
    │   └── DaySheets (many, allocated)
    ├── Invoices (many)
    ├── PurchaseOrders (many)
    ├── Timesheets (many)
    └── QARecords (many)

User
└── Tickets (many) — worker licenses
```

---

## Roadmap

| Phase | Focus | Key Deliverables |
|-------|-------|------------------|
| **V1.0** | Information Consolidation | OneDrive, Email Ingestion, Jobs Hub, Basic BI |
| **V2.0** | Automation Layer | Day Sheet OCR, Timesheet App, Ticket OCR |
| **V3.0** | Intelligence | Quote Builder, Contract Analysis, Forecasting |

---

## Document Standards

### Feature Spec Structure

```
1. CURRENT STATE (what exists today)
2. PROBLEM (what pain are we solving)
3. ENTITIES (what data structures)
4. INVARIANTS (what must always be true)
5. WORKFLOWS (step-by-step flows)
6. UI (key screens only)
7. INTEGRATION POINTS
8. OPEN QUESTIONS
```

### Status Key

- 🔴 TODO — Not started
- 🟡 IN PROGRESS — Being specified
- 🟢 COMPLETE — Ready for development

---

*This index provides navigation to all Quotech documentation.*

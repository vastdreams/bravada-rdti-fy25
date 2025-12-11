# Quotech — Data Model

> **Version**: 0.2 (First Principles)  
> **Last Updated**: December 2024

---

## Entity Hierarchy

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
                                                            │    │  │
                                                            └────┴──┘
```

---

## Core Entities

### Company

The root entity. One organisation using Quotech.

```
Company
  id              : UUID (PK)
  name            : String (required)
  abn             : String (optional, validated)
  onedrive_root   : String (required after onboarding)
  timezone        : String (default: "Australia/Sydney")
  settings        : JSON
  created_at      : DateTime
  updated_at      : DateTime
```

**Invariants:**
- Must have at least one User with role = `admin`
- `onedrive_root` must be set before creating Jobs

---

### User

A person using the system.

```
User
  id              : UUID (PK)
  company_id      : UUID (FK → Company)
  email           : String (unique, required)
  name            : String (required)
  role            : Enum {admin, pm, estimator, supervisor, accounts, viewer}
  permissions     : JSON (granular overrides)
  preferences     : JSON (UI state)
  created_at      : DateTime
```

**Invariants:**
- `email` unique across all users
- Exactly one `role`
- Belongs to exactly one Company

---

### Job

A construction project.

```
Job
  id                  : UUID (PK)
  company_id          : UUID (FK → Company)
  job_number          : String (unique per company)
  name                : String (required)
  status              : Enum {tender, quoted, won, active, complete, archived}
  client_name         : String
  site_address        : String
  onedrive_folder     : String (required)
  estimator_id        : UUID (FK → User, optional)
  project_manager_id  : UUID (FK → User, optional)
  start_date          : Date (optional)
  due_date            : Date (optional)
  contract_value      : Decimal (updated when variations approved)
  created_at          : DateTime
  updated_at          : DateTime
```

**Invariants:**
- `job_number` unique within company
- `status` follows lifecycle: tender → quoted → won → active → complete → archived
- `contract_value` = original_quote + sum(approved_variations)

---

### Quote

A pricing proposal for a job.

```
Quote
  id              : UUID (PK)
  job_id          : UUID (FK → Job)
  quote_number    : String (unique per job)
  version         : Integer (starts at 1)
  status          : Enum {draft, sent, accepted, rejected, expired}
  
  total_cost      : Decimal (calculated from CostItems)
  total_sell      : Decimal (calculated from CostItems)
  margin_percent  : Decimal (calculated)
  
  scope_text      : Text
  valid_until     : Date
  sent_date       : DateTime (null if draft)
  
  parent_id       : UUID (FK → Quote, for revisions)
  created_by      : UUID (FK → User)
  created_at      : DateTime
```

**Invariants:**
- `total_cost` = sum(CostItems.total_cost)
- `total_sell` = sum(CostItems.total_sell)
- `margin_percent` = (total_sell - total_cost) / total_sell × 100
- Revisions link to `parent_id`, increment `version`

---

### CostItem

A line item in a quote.

```
CostItem
  id              : UUID (PK)
  quote_id        : UUID (FK → Quote)
  section         : String (grouping label)
  description     : String (required)
  category        : Enum {labour, materials, plant, subcontractor, other}
  
  quantity        : Decimal
  unit            : String (m², hrs, each, etc.)
  unit_cost       : Decimal
  unit_sell       : Decimal
  
  total_cost      : Decimal (calculated)
  total_sell      : Decimal (calculated)
  
  sort_order      : Integer
```

**Invariants:**
- `total_cost` = quantity × unit_cost
- `total_sell` = quantity × unit_sell
- `category` is one of the 5 canonical categories

---

### Variation

A change to original job scope.

```
Variation
  id                  : UUID (PK)
  job_id              : UUID (FK → Job)
  variation_number    : String (unique per job, e.g., "V001")
  type                : Enum {scope_change, do_and_charge, mini_project}
  status              : Enum {draft, submitted, under_review, approved, rejected, invoiced}
  
  description         : Text
  reason              : Enum {client_request, design_change, site_condition, error, other}
  
  estimated_value     : Decimal
  approved_value      : Decimal (set when approved)
  
  submitted_date      : DateTime
  approved_date       : DateTime
  approved_by         : String (client approver name)
  
  linked_quote_id     : UUID (FK → Quote, for mini_project type)
  instruction_email_id: UUID (FK → Email, optional)
  
  created_by          : UUID (FK → User)
  created_at          : DateTime
```

**Invariants:**
- `type = do_and_charge` requires allocated DaySheets
- `type = mini_project` should have `linked_quote_id`
- When `status = approved`, `approved_value` flows to Job.contract_value

---

### DaySheet

Time & materials work record.

```
DaySheet
  id                  : UUID (PK)
  job_id              : UUID (FK → Job)
  variation_id        : UUID (FK → Variation, null until allocated)
  
  date                : Date
  shift_start         : Time
  shift_end           : Time
  total_hours         : Decimal (calculated)
  
  workers             : JSON [{user_id, name, hours, hourly_rate}]
  description         : Text
  materials           : JSON [{description, qty, unit_cost, total}]
  materials_total     : Decimal
  
  supervisor_id       : UUID (FK → User)
  client_name         : String
  client_signature_url: String
  signed_at           : DateTime
  sign_off_gps        : Point
  
  status              : Enum {draft, submitted, approved, rejected}
  scan_url            : String (original if OCR captured)
  pdf_url             : String (generated evidence)
  
  created_at          : DateTime
```

**Invariants:**
- Can be allocated to at most ONE Variation
- `status = submitted` requires client signature
- `total_hours` = sum(workers[].hours)
- Labour value = sum(workers[].hours × workers[].hourly_rate)

---

### File

A document in the job folder.

```
File
  id              : UUID (PK)
  job_id          : UUID (FK → Job)
  category        : Enum {contracts, quotes, invoices, bills, site, info, qa, other}
  
  onedrive_path   : String (full path)
  filename        : String
  file_type       : String (MIME)
  file_size       : Integer (bytes)
  version         : Integer
  
  search_text     : Text (extracted content)
  indexed_at      : DateTime
  
  uploaded_by     : UUID (FK → User)
  created_at      : DateTime
```

**Invariants:**
- `onedrive_path` must exist in customer's OneDrive
- `version` increments when same filename re-uploaded

---

### Email

A captured email.

```
Email
  id              : UUID (PK)
  job_id          : UUID (FK → Job)
  outlook_id      : String (original message ID)
  
  category        : Enum {same as File categories}
  subject         : String
  from_address    : String
  from_name       : String
  to_addresses    : Array[String]
  cc_addresses    : Array[String]
  received_at     : DateTime
  
  body_text       : Text
  body_html       : Text
  has_attachments : Boolean
  
  onedrive_path   : String (saved .eml location)
  ai_summary      : Text (optional)
  classified_by   : Enum {ai, user, rule}
  
  created_at      : DateTime
```

**Invariants:**
- `outlook_id` unique (no duplicate capture)
- Attachments extracted and saved as separate File entities

---

### Supplier

A vendor or subcontractor.

```
Supplier
  id              : UUID (PK)
  company_id      : UUID (FK → Company)
  name            : String (required)
  abn             : String (optional)
  email           : String
  phone           : String
  category        : String (materials, subcontractor, plant hire, etc.)
  payment_terms   : String
  created_at      : DateTime
```

---

### PurchaseOrder

An order to a supplier.

```
PurchaseOrder
  id              : UUID (PK)
  job_id          : UUID (FK → Job)
  supplier_id     : UUID (FK → Supplier)
  po_number       : String
  status          : Enum {draft, sent, acknowledged, delivered, complete}
  
  items           : JSON [{description, qty, unit_price, total}]
  total_value     : Decimal
  
  delivery_date   : Date
  sent_date       : DateTime
  created_by      : UUID (FK → User)
  created_at      : DateTime
```

---

### Invoice

An invoice for the job.

```
Invoice
  id              : UUID (PK)
  job_id          : UUID (FK → Job)
  invoice_number  : String
  type            : Enum {progress_claim, final, variation, retention_release}
  status          : Enum {draft, sent, approved, paid, overdue}
  
  amount          : Decimal
  gst             : Decimal
  total           : Decimal
  
  claim_period    : String
  due_date        : Date
  sent_date       : DateTime
  paid_date       : DateTime
  
  variation_id    : UUID (FK → Variation, optional)
  xero_id         : String (if synced)
  pdf_url         : String
  
  created_by      : UUID (FK → User)
  created_at      : DateTime
```

---

### Timesheet

Worker time entry.

```
Timesheet
  id              : UUID (PK)
  user_id         : UUID (FK → User)
  job_id          : UUID (FK → Job)
  
  date            : Date
  start_time      : Time
  end_time        : Time
  break_minutes   : Integer
  total_hours     : Decimal (calculated)
  
  gps_start       : Point
  gps_end         : Point
  notes           : Text
  
  status          : Enum {draft, submitted, approved, rejected}
  approved_by     : UUID (FK → User)
  approved_at     : DateTime
```

**Invariants:**
- `total_hours` = (end_time - start_time) - break_minutes/60

---

### Ticket

Worker license or certification.

```
Ticket
  id              : UUID (PK)
  user_id         : UUID (FK → User)
  
  type            : String (White Card, Forklift, EWP, etc.)
  license_number  : String
  issued_date     : Date
  expiry_date     : Date
  issuing_authority: String
  
  scan_url        : String
  verified        : Boolean
  ocr_data        : JSON
  
  created_at      : DateTime
```

**Invariants:**
- System should warn when `expiry_date` < now + 30 days

---

### QARecord

Quality assurance entry.

```
QARecord
  id              : UUID (PK)
  job_id          : UUID (FK → Job)
  
  type            : String (inspection, test, checklist)
  title           : String
  location        : String
  date            : Date
  
  inspector_id    : UUID (FK → User)
  status          : Enum {pass, fail, pending, na}
  findings        : Text
  
  photos          : Array[String] (URLs)
  signature_url   : String
  form_data       : JSON (structured checklist)
  
  created_at      : DateTime
```

---

## Enumerations Summary

| Enum | Values |
|------|--------|
| **JobStatus** | tender, quoted, won, active, complete, archived |
| **QuoteStatus** | draft, sent, accepted, rejected, expired |
| **VariationType** | scope_change, do_and_charge, mini_project |
| **VariationStatus** | draft, submitted, under_review, approved, rejected, invoiced |
| **DaySheetStatus** | draft, submitted, approved, rejected |
| **CostCategory** | labour, materials, plant, subcontractor, other |
| **FileCategory** | contracts, quotes, invoices, bills, site, info, qa, other |
| **UserRole** | admin, pm, estimator, supervisor, accounts, viewer |

---

## Key Calculations

### Job Profitability

```
Contract Value = Original Quote + Sum(Approved Variations)
Revenue to Date = Sum(Invoices where status in [sent, approved, paid])
Cost to Date = Sum(Timesheets × rate) + Sum(Supplier Bills)
Gross Profit = Revenue - Cost
Margin % = Gross Profit / Revenue × 100
```

### Quote Margin

```
Total Cost = Sum(CostItem.quantity × CostItem.unit_cost)
Total Sell = Sum(CostItem.quantity × CostItem.unit_sell)
Margin % = (Total Sell - Total Cost) / Total Sell × 100
```

### Day Sheet Value (Do-and-Charge)

```
Labour Value = Sum(worker.hours × worker.hourly_rate)
Total Value = Labour Value + Materials Total + GST
```

---

*This data model defines the entities, relationships, and invariants for Quotech. All feature implementations must respect these constraints.*

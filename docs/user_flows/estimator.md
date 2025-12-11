# User Flow: Estimator

> **Persona**: Estimator / Quantity Surveyor  
> **Primary Modules**: Quotes & Tenders, Variations

---

## Role Summary

Creates quotes, manages tender pipeline, prices variations.

| Responsibility | Module |
|----------------|--------|
| Create quotes | Quotes & Tenders |
| Manage pipeline | Quotes & Tenders |
| Price variations | Variations |
| Analyze win/loss | BI |

---

## Daily Workflow

```
1. Check pipeline → quotes awaiting action
2. Review new tenders → create jobs, start quotes
3. Follow up on sent quotes → chase approvals
4. Price variation requests → from PMs
5. Analyze lost quotes → improve future pricing
```

---

## Key Workflows

### 1. New Tender → Quote

```
Tender Received → Create Job (status: tender) → Review Scope → Build Quote → Review/Finalize → Generate PDF → Send to Client
```

| Step | Detail |
|------|--------|
| Create Job | Status = tender, attach tender docs |
| Review Scope | Drawings, specs, site info |
| Build Quote | Sections + cost items |
| Finalize | Check margin, add scope text |
| Send | Email from system (auto-captured) |

### 2. Quote Cost Items

```
Add Section → Add Items → Enter: Description, Category, Qty, Unit, Cost, Sell → Calculate Totals
```

| Category | Examples |
|----------|----------|
| Labour | Installation hrs, supervision |
| Materials | Products, consumables |
| Plant | Equipment hire |
| Subcontractor | External trades |
| Other | Permits, contingency |

### 3. Quote Revision

```
Feedback Received → Create Revision (links to parent) → Adjust Items → Send New Version
```

### 4. Quote → Active Job

```
Quote Accepted → Mark Won → Job Status → "won" → Handoff to PM → Job Status → "active"
```

### 5. Variation Pricing

```
PM Requests Pricing → Review Scope Change → Create Variation Quote → Send Back to PM
```

---

## Pipeline View

```
DRAFT (3)     SENT (5)      PENDING (2)     WON (8)     LOST (4)
$450K         $1.2M         $380K           $2.1M       $680K
```

### Actions by Status

| Status | Actions |
|--------|---------|
| Draft | Edit, Delete, Send |
| Sent | Track, Revise |
| Pending | Chase, Revise |
| Won | View, Handoff |
| Lost | Record reason, Archive |

---

## Success Metrics

| Metric | Target |
|--------|--------|
| Win rate | > 50% |
| Quote turnaround | < 5 days |
| Revision count | < 2 avg |
| Margin accuracy | ± 5% |

---

## Pain Points Solved

| Before | After |
|--------|-------|
| Quotes in Excel | Structured system |
| Pipeline in spreadsheet | Kanban view |
| No win/loss tracking | Built-in analytics |
| Copy-paste errors | Templates + validation |
| Lost context on handoff | Quote → Job data flows |
